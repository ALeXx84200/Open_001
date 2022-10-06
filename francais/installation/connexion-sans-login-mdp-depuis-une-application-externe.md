# Connexion sans login/mdp depuis une application externe

Dans certains cas vous pouvez avoir besoin d'accéder à Open-Capture sans passer par une authentification (de la meme manière qu'un SSO). Cela sera possible via la génération d'un token JWT par votre application dans laquelle vous souhaitez intégrer **Open-Capture**.&#x20;

Pour commencer, il vous faudra récupérer la clé secrète de votre instance d'**Open-Capture**, générée de manière aléatoire lors de l'installation. Cette dernière est située dans le dossier custom de votre instance, dans le sous dossier `config`.

```
/var/www/html/opencapture/custom/edissyum/config/secret_key
```

Il vous suffira ensuite de générer le token à l'aide de cette clé secrète ainsi que du username de l'utilisateur (pour cela veillez bien à ce que les username Open-Capture et de l'application externe soient similaires. Soit via l'utilisation du LDAP, soit à la main en étant très vigilant). Vous retrouverez ci-dessous un exemple d'une fonction générant le token en Python, Javascript ainsi qu'en PHP.

{% hint style="info" %}
Par défaut les tokens ont une durée de validité d'une journée (1440 minutes)
{% endhint %}

{% tabs %}
{% tab title="Code Python" %}
```python
import jwt
from datetime import datetime, timedelta

def encode_token(user_id, secret_key):
    try:
        payload = {
            'exp': datetime.utcnow() + timedelta(minutes=1440, seconds=0),
            'iat': datetime.utcnow(),
            'sub': user_id
        }
        return jwt.encode(
            payload,
            secret_key,
            algorithm='HS512'
        )
    except Exception as _e:
        return str(_e)
```
{% endtab %}

{% tab title="Code PHP" %}
```php
require('vendor/firebase/php-jwt/src/JWT.php');
use \Firebase\JWT\JWT;

function generate_token($user_id, $secret_key) {
    $issuedAt = new DateTimeImmutable();
    $payload = [
        'exp' => $issuedAt -> modify('+1440 minutes') -> getTimestamp(),
        'iat' => $issuedAt -> getTimestamp(),
        'sub' => $user_id
    ];
    return $jwt = JWT::encode($payload, $secret_key, 'HS512');
}
```
{% endtab %}

{% tab title="Code Javascript" %}
```javascript
function base64url(source) {
    let encodedSource = CryptoJS.enc.Base64.stringify(source);
    encodedSource = encodedSource.replace(/=+$/, '');
    encodedSource = encodedSource.replace(/\+/g, '-');
    encodedSource = encodedSource.replace(/\//g, '_');
    return encodedSource;
}

function generate_token(user_id, secret_key) {
    const header = {
        "alg": "HS512",
        "typ": "JWT"
    };
    const stringifiedHeader = CryptoJS.enc.Utf8.parse(JSON.stringify(header));
    const encodedHeader = base64url(stringifiedHeader);
    const today = new Date()
    const expDate = today.setMinutes(today.getMinutes() + 1440);
    const data = {
        'exp': expDate,
        'iat': today.valueOf(),
        "sub": user_id
    };
    const stringifiedData = CryptoJS.enc.Utf8.parse(JSON.stringify(data));
    const encodedData = base64url(stringifiedData);
    const token = encodedHeader + "." + encodedData;
    let signature = CryptoJS.HmacSHA512(token, secret_key);
    signature = base64url(signature);
    return token + "." + signature;
}
```
{% endtab %}
{% endtabs %}

Il ne vous restera plus qu'à stocker ce token dans un cookie, qui sera lu par **Open-Capture** pour procéder à la connexion automatique. Vous retrouverez ci-dessous un exemple simple en javascript, il ne vous restera plus qu'à remplacer la variable `token` par le token précédemment généré, de la manière la plus pratique pour vous.

{% hint style="info" %}
Le nom du cookie intègre l'identifiant de votre custom, `edissyum` ici en l'occurence. Pensez à le modifier au besoin
{% endhint %}

```javascript
setCookie(cname: string, cvalue: string, expMinutes: number) {
    const d = new Date();
    if (exdays !== 0) {
        d.setMinutes(d.getMinutes() + expMinutes);
        const expires = "expires=" + d.toUTCString();
        document.cookie = cname + "=" + cvalue + ";" + expires + ";path=/;SameSite=Strict";
    } else {
        document.cookie = cname + "=" + cvalue + ";path=/;SameSite=Strict";
    }
}

setCookie('OpenCaptureToken_edissyum', token, 1);
```
