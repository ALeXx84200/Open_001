# Masques de positionnement

Les masques de positionnement permettent de spécifier les emplacements des différents champs d'une facture pour un fournisseur. Cela est utile pour un fournisseur disposant d'un affichage offrant de mauvais résultats avec des REGEX. Cela permet également d'augmenter les temps de traitements, car le logiciel ira directement chercher dans la facture au bon endroit plutôt que de balayer toute la facture.

{% hint style="info" %}
/!\ Si les données bougent de place entre le masque de positionnement et la facture courante, les données risquent d'être erronées /!\\
{% endhint %}

![Masques de positionnement](../../.gitbook/assets/2022-03-25\_16-19.png)

Depuis l'interface de modification vous aurez la possibilité de choisir un libellé ainsi que le fournisseur associé à ce masque de positionnement. Il ne vous reste ensuite plus qu'à sélectionner un PDF du fournisseur.

![Créer un masque](../../.gitbook/assets/2022-03-31\_11-22.png)

Vous êtes ensuite face à une interface ressemblant à l'interface de vidéo-codage d'une facture. Sur la droite vous retrouverez les différents champs de base mais également les champs personnalisés. Pour faire apprendre un champ, il vous suffit de le sélectionner sur la droite et ensuite de dessiner avec votre souris sur l'image à gauche au bon endroit.&#x20;

![Différents masques de positionnement](../../.gitbook/assets/2022-03-31\_11-15.png)
