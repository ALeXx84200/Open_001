# Chaînes entrantes

La liste des chaines entrantes rassemble les différentes chaines entrantes de l'application. Depuis cette dernière il vous sera possible de voir rapidement l'identifiant technique, le libellé technique (utilisé dans les scripts), le libellé ainsi que le chemin de capture.

![Chaîne entrante](../../.gitbook/assets/2022-03-25\_16-16.png)

Lors de la création, vous pourrez renseigner les champs vu plus tôt mais également le formulaire par défaut associé, le compte client ainsi que le type de facture (achat ou vente) et également la méthode de séparation. Lorsque vous mettez un chemin de capture, l'application tentera de créer le dossier s'il n'existe pas. Ensuite un script sera créé automatiquement et un job sera rajouté dans le fichier de paramétrage du fs-watcher qui s'occupera de lancer le script dès qu'un fichier est déposé dans le dossier. Enfin, vous pourrez choisir de supprimer les pages blanches et également d'outrepasser le formulaire par défaut du fournisseur, si ce dernier est trouvé de manière automatique.

![Ajouter des chaînes](<../../.gitbook/assets/2022-03-25\_16-17 (1).png>)

