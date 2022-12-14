# Création d'instances supplémentaires

Dans le cas d'une installation multi-instances, vous serez forcément obligé de créer d'autres customs. Cette partie est grandement facilitée grâce à l'utilisation d'un script permettant d'effectuer toutes les actions de copier-coller de documents, etc.. Il vous faudra simplement spécifier lors de l'appel au script le nom de la nouvelle instance (`edissyum_bis` dans notre exemple) ainsi que le type d'installation (entre `systemd` et `supervisor`).

```bash
cd /var/www/html/opencapture/bin/install/
sudo ./create_custom.sh -c edissyum_bis -t systemd
    ou
sudo ./create_custom.sh -c edissyum_bis -t supervisor
```

Le script va vous demander les informations de connexion à la base de données : Adresse de la BDD, port de la BDD, nom d'utilisateur et mot de passe. Merci de préciser un identifiant qui n'existe pas déjà. Finalement ce serait le chemin de base des docservers ainsi que le mot de passe de l'utilisateur postgres qui vous sera demandé (par défaut, postgres)

De nouveaux chemins de docservers seront créés également, afin de séparer les documents des différentes instances.

```
/var/docservers/OpenCapture/edissyum_bis/
```

## Accès à votre installation

Sur une installation classique comme ici, vous pourrez directement accéder à votre instance via l'adresse IP de votre serveur (ou nom de domaine).&#x20;

> exemple : http://192.168.10.10/edissyum\_bis/dist/

{% hint style="info" %}
Notez bien la présence d'un nom de l'instance `edissyum` dans l'URL, ceci est indispensable.
{% endhint %}
