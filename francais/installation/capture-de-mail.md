# Capture de mail

Si nécessaire, il est possible de capturer les factures directement depuis votre boîte mail. Ce seront seulement les pièces jointes des différents e-mails qui seront récupérées, si elles sont au format PDF. Afin de connecter votre boîte mail, il sera nécessaire de se procurer les informations IMAP de cette dernière. Il vous faudra renseigner l'adresse IMAP du serveur de mail, son port, si le SSL doit être activé et le combo utilisateur/mot de passe.

Il est possible de paramétrer plusieurs chaaines de captures, vous retrouverez la procédure dans la partie spécifique [aux processus MailCollect](../../parametrages/reglages-generaux/mailcollect.md).

## Paramétrage de la tache planifiée

Afin que le script de capture de mail puisse se lancer, il va falloir le mettre en tâche planifiée. Pour cela rien de plus simple avec les crontab. Par exemple la crontab ci-dessous va vous lancer la capture de mail toutes les 5 minutes, de 8h à 18h du lundi au vendredi. Vous pouvez bien entendu la modifier au besoin. Il ne vous reste plus qu'à lancer la commande crontab -e et à rajouter cette ligne.

{% hint style="info" %}
Pensez bien à modifier l'identifiant du custom, `edissyum` dans l'exemple ci-dessous.
{% endhint %}

{% code title="crontab -e" %}
```bash
*/5 8-18 * * 1-5 /var/www/html/opencapture/custom/edissyum/bin/scripts/launch_MAIL.sh &> /dev/null
```
{% endcode %}

Pour finir et afin de nettoyer les fichiers de chaque captures de mai vous pouvez mettre en place le script de nettoyage suivant, toujours via les taches planifiés

{% code title="crontab -e" %}
```bash
0 2 * * * /var/www/html/opencapture/custom/edissyum/bin/scripts/MailCollect/clean.sh &> /dev/null
```
{% endcode %}
