# Installation TEST
 
## Prérequis

Afin de procéder à l'installation d'**Open-Capture** il est recommandé d'utiliser la distribution Debian en version 11.X. Cependant il reste possible d'utiliser les distributions Ubuntu et Ubuntu Server mais le support au niveau des bugs ne sera pas possible.&#x20;

Vous trouverez ci-dessous un tableau des versions Python & Tesseract testées avec **Open-Capture**.

| Python | Tesseract |
| ------ | --------- |
| 3.7.X  | 4.0.0     |
| 3.8.5  | 4.1.1     |
| 3.9.2  | 5.2.0     |
| 3.10.4 |           |

Pour la partie utilisation client, il est recommandé d'utiliser le navigateur Firefox. Chrome et Edge peuvent causer des problèmes.

## Clonage du dépôt git

C'est parti pour l'installation. Il n'y a rien de plus simple, vous n'avez qu'à taper les commandes suivantes. Ces dernières permettront :

* La création du dossier **Open-Capture**
* La mise en place des bons droits sur ce dossier
* L'installation de git&#x20;
* La récupération du dernier tag  &#x20;

```bash
sudo mkdir -p /var/www/html/opencapture/
sudo chmod -R 775 /var/www/html/opencapture/
sudo chown -R $(whoami):$(whoami) /var/www/html/opencapture/
sudo apt install -y git crudini
latest_tag=$(git ls-remote --tags --sort="v:refname" https://github.com/edissyum/opencapture.git | tail -n1 |  sed 's/.*\///; s/\^{}//' | grep -E '2.+([0-9])$')
git clone -b $latest_tag https://github.com/edissyum/opencapture/ /var/www/html/opencapture/
cd /var/www/html/opencapture/bin/install/
```

## Lancement de l'installateur

Vous êtes désormais prêt à installer tout le nécessaire pour faire fonctionner **Open-Capture**. Rien de bien compliqué, il vous suffira de quelques commandes seulement. Durant l'installation vous aurez le choix entre l'utilisation de [**systemd**](https://doc.ubuntu-fr.org/systemd) ou de [**supervisor**](https://doc.ubuntu-fr.org/systemd).

Par défaut c'est **systemd** qui sera choisi, offrant une traitement des factures une par une. De son côté, **supervisor** permettra de lancer en simultané X instances d'**Open-Capture**. Attention, si vous choisissez **supervisor**, la configuration de la machine devra suivre au niveau des performances.&#x20;

Le paramètre \`-c\` permet de spécifier le nom du custom (où seront stocké vos différents paramètres). Par défaut nous le mettons à "edissyum". Si vous souhaitez le changer, modifier le libellé dans la commande ci-dessous (éviter les espaces, accents et autres caractères spéciaux). À noter que si vous souhaitez installer Open-Capture sur un serveur accessible depuis l'extérieur, le custom peut prendre le nom de votre nom de domaine. (Exemple d'une commande pour l'instance https://demo.open-capture.com/ : `sudo ./install.sh -c demo.open-capture.com`

{% hint style="info" %}
Merci de ne pas lancer l'installateur avec l'utilisateur `root`. Il faut créer un utilisateur spécifique si aucun n'est déjà présent et lancer l'installateur en `sudo`.
{% endhint %}

{% hint style="info" %}
Si votre custom contient des `.` ou des `-`, l'application remplacera ces caractères par des `_`. Ne vous inquiétez pas, l'utilisation du nom du custom restera avec les caractères d'origines.&#x20;
{% endhint %}

```bash
chmod u+x install.sh
sudo ./install.sh -c edissyum
```

Si jamais vous souhaitez utiliser une langue d'OCR différente du français ou de l'anglais, il vous sera possible de télécharger les paquets supplémentaires de Tesseract. Pour cela il vous suffit d'aller [**sur le site suivant**](https://www.macports.org/ports.php?by=name\&substr=tesseract-) et de récupérer le code de langue situé après le `-`. Lancez ensuite la commande suivante :&#x20;

```bash
sudo apt install tesseract-ocr-<langcode>
```

## Accès à votre installation

Sur une installation classique comme ici, vous pourrez directement accéder à votre instance via l'adresse IP de votre serveur (ou nom de domaine).&#x20;

> Exemple : http://192.168.10.10/edissyum/dist/

{% hint style="info" %}
Notez bien la présence d'un nom de l'instance `edissyum` dans l'URL, ceci est indispensable.
{% endhint %}
