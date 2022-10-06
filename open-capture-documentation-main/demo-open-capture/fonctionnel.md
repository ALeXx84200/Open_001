# Fonctionnel

Si vous souhaitez découvrir **Open-Capture**, une plateforme de démonstration en ligne est disponible à l'adresse suivante : [https://demo.open-capture.com](https://kutt.it/DemoOC\_V2). Vous arriverez sur l'interface de connexion. La combinaison login / mot de passe par défaut est également présente (**admin** / **admin**).&#x20;

![Page de connexion](<../.gitbook/assets/Capture d’écran 2022-05-18 093159.png>)

Après la connexion effectuée, vous arriverez sur la page vous permettant de choisir entre deux modules :&#x20;

* **Open-Capture Splitter,** qui est le module de séparation intelligente
* **Open-Capture Verifier,** qui est le cœur d'Open-Capture avec, entre autres, l'interface de vidéo codage.

![Accueil](<../.gitbook/assets/Capture d’écran .png>)

### Open-Capture Splitter

En sélectionnant le module **Open-Capture Splitter** vous arriverez sur la page d’accueil du module, affichant les lots déjà téléversés.

![Module Splitter](<../.gitbook/assets/Capture d’écran 2022-05-18 093726.png>)

On peut apercevoir différents paramètres, comme la sélection des statuts différents. Pour commencer on a les lots à valider, qui contient donc les nouveaux lots qui ne sont pas validés. Ensuite, on a les lots clôturés qui font référence aux lots déjà validés. Puis les lots supprimés et enfin les lots fusionnés. La partie fusionnée contient la fusion de différents lots. Ces différents lots resteront malgré tout dans la partie "A valider".

Pour téléverser un document, il faudra se rendre sur la page **Téléversement.** Vous n'avez plus qu'à faire du glisser / déposer ou cliquer sur l'encart pour choisir le ou les document(s) à téléverser. Après un petit temps d'attente (dépendant de la complexité et du poids de la facture envoyée), la facture sera disponible dans l'accueil, accessible en cliquant sur **Lot**. Voici un exemple de lot de documents à utiliser dans le module **Open-Capture Splitter** : [Cliquez ici](https://kutt.it/DownloadSplitterFile).

![Téléversement](<../.gitbook/assets/Capture d’écran 2022-05-18 095137.png>)

En cliquant sur un lot, nous arrivons dans l'interface de vérification. Cette dernière vous montre les documents qui ont été séparés automatiquement. Vous pourrez valider la séparation, ou modifier si nécessaire. Il sera possible de déplacer les pages vers d'autres documents, supprimer des pages, ou encore créer des documents.

![Modification des lots](<../.gitbook/assets/Capture d’écran 2022-05-18 094950.png>)

De plus, vous pouvez sélectionner plusieurs dossier pour les envoyer vers des documents différents, faire une rotation de ces fichiers, les supprimer ou rajouter des dossiers. Ci-dessous, un exemple de déplacement de fichier ; où les deux fichiers qui ont était sélectionner vont être envoyé vers le document "Facture". Il suffit juste de cocher les deux fichiers et d'aller dans le paramètre "Envoyer à" et de sélectionner quel documents.

![Exemple](<../.gitbook/assets/Capture d’écran 2022-05-18 095643.png>)

De plus, vous pouvez voir qu'au dessus de la corbeille il y a le nombre de fichier sélectionnés. Cette page vous permet aussi d'enregistrer votre sélection, ce qui va vous permettre de revenir après sans perdre vos changements.

Vous pouvez aussi changer le formulaire et les métadonnées qui sont insérées par défaut, en rajouter ou en supprimer : [Listes des formulaires](../parametrages/reglages-splitter/formulaires.md)

![Après avoir appuyé sur "Valider"](<../.gitbook/assets/Capture d’écran 2022-05-18 100106.png>)

Dès que tout est validé, il vous suffira de cliquer sur le bouton **Valider** pour valider la séparation. Ensuite, les documents et le fichier compagnon contenant les métadonnées seront exportés selon la ou[ les chaine(s) sortante(s)](../parametrages/reglages-splitter/chaines-sortantes.md) configurée(s). Le temps de traitement dépendra de la complexité et de la taille des documents.

## Open-Capture Vérifier

Viens maintenant la dernière étape du processus. Dans l'écran d’accueil vous retrouverez les différents lots scannés. Nous retrouverons différentes informations en fonction des métadonnées récupérées automatiquement durant le téléversement :&#x20;

* Nom du fournisseur
* Numéro de facture
* Date de facture
* Fichier d'origine (indépendant de la récupération automatique des méta données)
* Date d'enregistrement de la facture (indépendant de la récupération automatique des méta données)

De plus, sur la partie gauche de la page, on peut apercevoir le tri des fichiers par clients avec les dossiers pour chaque types de factures

![Page d'accueil](<../.gitbook/assets/Capture d’écran 2022-05-18 102433.png>)

Une fois après avoir sélectionner un lot, vous arrivez dans la page ci-dessous : &#x20;

![Validation du lots](<../.gitbook/assets/Capture d’écran 2022-05-18 100418.png>)

Ici, on peut apercevoir tous les paramètres de la facture, là où le logiciel les a trouvé grâce aux [Regex](../parametrages/reglages-generaux/regex.md). Vous pouvez donc vérifier si les informations relevées sont correcte ou les changé en déplaçant les rectangles qui correspondent aux données ou les rentrer manuellement.

A la fin de la vérification, vous pouvez valider la facture ou la refuser. Vous retrouverez cette facture dans les différents statuts du module Vérifier :  &#x20;

![Module Verifier](<../.gitbook/assets/Capture d’écran 2022-05-18 101034.png>)

Dans le statuts "Clôturée" se trouve les fichiers qui ont été validés, dans "Erreur", on retrouve ceux qui ont été refusés et enfin, on a ceux qui ont été supprimés.

## Télécharger des factures d'essais

Si vous souhaitez essayer l'outil, nous vous donnons accès à des factures que vous pouvez utiliser en les téléversant dans l'outil. Vous pourrez les télécharger en [cliquant ici](https://kutt.it/DownloadInvoices).
