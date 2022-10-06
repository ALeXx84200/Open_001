# Méthodes d'authentification

OpenCapture permet d'exploiter un annuaire de type AdLDAP ou OpenLDAP afin de centraliser la gestion des utilisateurs.

Deux niveaux d'exploitation possibles:

* Authentification LDAP, la vérification des mots de passe des utilisateurs se fait dans l'annuaire dans ce cas.
* Synchronisation des données de l'annuaire dans la base Opencapture.

Le menu des méthodes authentification rassemble les différents types d'authentification disponibles. Cette page permet de voir directement toutes les méthodes qu'un administrateur peut activer ou désactiver.

![](../../.gitbook/assets/capture\_doc1.png)

La méthode d’authentification "défaut" est celle qui est activée par défaut. Elle permet la connexion simple depuis la base de données d'Open-Capture For Invoices.

### Activation de la méthode d'authentification LDAP

Une fois que le bouton d'activation est sélectionné, il faut remplir les paramètres de connexion et tester la connexion au serveur LDAP. La partie "Synchronisation" contient tous les paramètres nécessaires pour la synchronisation des utilisateurs.

![Connexion](../../.gitbook/assets/capture\_doc7.png)

![Synchronisation](../../.gitbook/assets/capture\_doc3.png)

Il existe un script python dont le chemin depuis le répertoire d'installation OpenCapture  est le suivant  /bin/ldap/connectionLdapTest/connection\_ldap.py . Le script permet de récupérer les paramètres de synchronisation.

Pour lancer le script : python3 connection\_ldap.py&#x20;

![Sortie script python](../../.gitbook/assets/capture.png)

Exemple :&#x20;

* givenName : Attribut prénom utilisateur
* sn : Attribut nom utilisateur&#x20;
* uid : Attribut source utilisateur
* objectClass : Classe objet
* inetOrgPerson : Classe utilisateur

Lorsque tous les champs obligatoires sont remplis, l'administrateur peut  lancer l'opération de synchronisation via le bouton "Lancer" dans la partie "Lancement".

![Lancement](../../.gitbook/assets/capture\_doc4.png)

Le bouton "Enregistrer" sera cliquable seulement si le test de connexion et l'opération de synchronisation sont valides.

En cliquant sur ce dernier, toutes les informations (celles de connexion et aussi celles de synchronisation) seront enregistrées dans la base de données Opencapture dans la table **login\_methods**. (Au chargement de la page, tous les champs seront remplis avec les données déjà enregistrées)

Si la méthode d'authentification LDAP est activé,  un message "LDAP activé"  va apparaître en dessous du formulaire de connexion.

![](../../.gitbook/assets/capture\_doc5.png)

### &#x20;

