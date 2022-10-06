---
description: Administration des chaînes sortantes du module Splitter
---

# Chaînes sortantes

Cette page vous permet de gérer la destination des documents validés dans le Splitter.

![Chaînes sortantes](../../.gitbook/assets/2022-05-11\_17-07.png)

Pour ajouter une chaîne cliquez sur “Ajouter une chaîne sortante”, ensuite remplissez les champs :

![Création d'une chaîne sortante](../../.gitbook/assets/2022-05-11\_17-09.png)

Les champs à configurer sont :

*   **Type de chaîne sortante :**

    _<mark style="color:blue;"></mark>_

_<mark style="color:blue;">Export PDF :</mark> _ exporter les fichiers PDF résultats de la séparation.

_<mark style="color:blue;">Export XML :</mark>_ exporter le fichier XML compagnon contenant l’ensemble de métadonnées associées au lot.

Pour les deux types de chaîne sortante des paramètres supplémentaires sont nécessaires dans la fenêtre “spécifiques”, ci-dessous les champs à configurer:

* Dossier de sortie : Chemin du dossier utilisé pour exporter les fichiers.&#x20;
* Nom du fichier : masque de nommage du fichier contenant la liste des identifiants techniques des champs disponibles séparés par “#”.&#x20;
* Séparateur : caractère de séparation des champs utilisés dans le nom du fichier
* Extension : xml ou pdf.

_<mark style="color:blue;">Export Alfresco :</mark>_ Envoyer la paire PDF/XML vers une instance Alfresco.

Pour ce type de chaîne sortante des paramètres supplémentaire sont nécessaires dans la fenêtre “Authentification”, ci-dessous les champs à configurer :

* CMIS Web-Service : URL du Web-Service type CMIS Browser.
* Répertoire de dépôt : Chemin du répertoire accessible depuis le Web-service CMIS.&#x20;
* Pseudo de l’utilisateur WS : utilisateur Alfresco ayant les droits de consommer le Web-Service.&#x20;
* Mot de passe de l’utilisateur WS : Mot de passe de l’utilisateur Alfresco.

Après avoir saisi tous les champs ci-dessus, vous pouvez effectuer un test de connexion.

* **Libellé :** nom de la chaîne sortante.
* **Type de compression** (Affiché seulement si le type Export PDF est sélectionné) **:** Niveau de compression des fichiers PDF après une validation d’un lot.
