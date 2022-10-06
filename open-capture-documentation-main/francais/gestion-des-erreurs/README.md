# Gestion des erreurs

Si vous rencontrez des erreurs, il y a plusieurs endroits où aller regarder afin de déterminer la cause du problème. Le premier endroit est le fichier de log principal. Il recense tout ce qu'il se passe dans le traitement d'**Open-Capture**, même lorsqu'il n'y a pas d'erreurs. Ci-dessous des exemples de logs en fonction de l'installation (via systemd ou via supervisor). Pour les mails, les fichiers de logs sont situés dans `/var/www/html/opencapture/bin/data/MailCollect/*BATCH_NAME*`. Les logs sont ensuite séparés par jours.

{% tabs %}
{% tab title="systemd" %}
{% code title="/var/www/html/opencapture/bin/data/log/OCForInvoices.log" %}
```bash
[Open-Capture  ] 19-03-2021 17:03:59 INFO Processing file : /home/nathan/PycharmProjects/oc_invoices_flask/bin/data/exported_pdf//tmpov9aco7h/Facture_OpenNetWork_3.pdf
[Open-Capture  ] 19-03-2021 17:04:17 INFO Supplier found : Edissyum using VAT Number : FR71510268261
[Open-Capture  ] 19-03-2021 17:04:17 INFO Invoice number not found. Searching invoice number using position in database
[Open-Capture  ] 19-03-2021 17:04:17 INFO Invoice number found with position : 400019
[Open-Capture  ] 19-03-2021 17:04:17 INFO Due date found : 07/01/2012
[Open-Capture  ] 19-03-2021 17:04:17 INFO Invoice date found : 31/12/2011
[Open-Capture  ] 19-03-2021 17:04:20 INFO Footer informations found : [TOTAL : 10101.99] - [HT : 8348.75] - [VATRATE : 21.0]
[Open-Capture  ] 19-03-2021 17:04:20 INFO Order number found with position : 400019
[Open-Capture  ] 19-03-2021 17:04:21 INFO Invoice inserted in database
[Open-Capture  ] 19-03-2021 17:04:21 INFO All the usefull informations are found. Export the XML and end process
[Open-Capture  ] 19-03-2021 17:04:21 INFO Process end after 00:00:24.39
[Open-Capture  ] 19-03-2021 17:29:37 ERROR SQLITE connection error: unable to open database file

```
{% endcode %}
{% endtab %}

{% tab title="supervisor" %}
{% code title="/var/www/html/opencapture/bin/data/log/Supervisor/OCForInvoices_worker_00_error.log" %}
```
[Open-Capture  ] 19-03-2021 17:03:59 INFO Processing file : /home/nathan/PycharmProjects/oc_invoices_flask/bin/data/exported_pdf//tmpov9aco7h/Facture_OpenNetWork_3.pdf
[Open-Capture  ] 19-03-2021 17:04:17 INFO Supplier found : Edissyum using VAT Number : FR71510268261
[Open-Capture  ] 19-03-2021 17:04:17 INFO Invoice number not found. Searching invoice number using position in database
[Open-Capture  ] 19-03-2021 17:04:17 INFO Invoice number found with position : 400019
[Open-Capture  ] 19-03-2021 17:04:17 INFO Due date found : 07/01/2012
[Open-Capture  ] 19-03-2021 17:04:17 INFO Invoice date found : 31/12/2011
[Open-Capture  ] 19-03-2021 17:04:20 INFO Footer informations found : [TOTAL : 10101.99] - [HT : 8348.75] - [VATRATE : 21.0]
[Open-Capture  ] 19-03-2021 17:04:20 INFO Order number found with position : 400019
[Open-Capture  ] 19-03-2021 17:04:21 INFO Invoice inserted in database
[Open-Capture  ] 19-03-2021 17:04:21 INFO All the usefull informations are found. Export the XML and end process
[Open-Capture  ] 19-03-2021 17:04:21 INFO Process end after 00:00:24.39
[Open-Capture  ] 19-03-2021 17:29:37 ERROR SQLITE connection error: unable to open database file
```
{% endcode %}
{% endtab %}

{% tab title="MailCollect" %}
{% code title="bin/data/MailCollect/MAIL_1/20210406/BATCH_20210406_142651576284_daycputd/20210406_142651576284.log" %}
```
[Open-Capture  ] 06-04-2021 14:26:51 INFO Start following batch : BATCH_20210406_142651576284_daycputd
[Open-Capture  ] 06-04-2021 14:26:51 INFO Action after processing e-mail is : none
[Open-Capture  ] 06-04-2021 14:26:51 INFO Number of e-mail to process : 8
[Open-Capture  ] 06-04-2021 14:26:51 INFO Start to process only attachments
[Open-Capture  ] 06-04-2021 14:26:51 INFO Process e-mail n°1/2
[Open-Capture  ] 06-04-2021 14:26:51 INFO Found 1 attachments
[Open-Capture  ] 06-04-2021 14:26:51 INFO Process attachment n°1/1
[Open-Capture  ] 06-04-2021 14:26:52 INFO Processing file : /home/nathan/PycharmProjects/oc_invoices_flask/bin/data/MailCollect//MAIL_1/20210406/BATCH_20210406_142651576284_daycputd/mail_9/attachments/Plans_Bailleur_ST_NAZAIRE_IMMACULÉE_V2_220321.pdf
[Open-Capture  ] 06-24-2021 14:27:47 INFO Supplier found : Edissyum using VAT Number : FR71510268261
[Open-Capture  ] 06-04-2021 14:28:11 INFO Invoice date found : 16/03/2021
[Open-Capture  ] 06-04-2021 14:28:35 INFO Invoice inserted in database
[Open-Capture  ] 06-04-2021 14:28:35 INFO Process end after 00:01:44.23
[Open-Capture  ] 06-04-2021 14:28:35 INFO Process e-mail n°2/2
[Open-Capture  ] 06-04-2021 14:28:35 INFO No attachments found
[Open-Capture  ] 06-04-2021 14:28:35 INFO Start to process only attachments
```
{% endcode %}
{% endtab %}
{% endtabs %}

Si jamais une erreur apparait dans l'interface web, vous empêche toute action et que rien n'est présent dans les fichiers de logs, il faudra aller regarder du côté les logs d'erreurs du service \`apache2\`. Vous pourrez voir l'erreur en utilisant la commande suivante. Avec cette erreur, vous pouvez ouvrir une [**issue** sur le github](https://kutt.it/OCForInvoices\_ISSUES) afin que nous puissions l'investiguer.

```bash
sudo tail -f /var/log/apache2/error.log
```

Si jamais le problème intervient lors du traitement de la facture (cette dernière ne remonte pas dans l'interface par exemple), ce sera le service gérant **Open-Capture-Splitter** ou **Open-Capture-Vérifier** qu'il faudra vérifier. Comme pour la partie web, avec les informations sur l'erreur, vous pouvez ouvrir une [**issue** sur le github](https://kutt.it/OCForInvoices\_ISSUES).

{% tabs %}
{% tab title="Open-Capture Verifier" %}
```bash
sudo systemctl status OCVerifier-worker_CUSTOMID
```
{% endtab %}

{% tab title="Open-Capture Splitter" %}
```
sudo systemctl status OCSplitter-worker_CUSTOMID
```
{% endtab %}
{% endtabs %}

Si vous êtes capable de corriger le problème vous-même, il faudra bien penser à redémarrer le service en question afin que les modifications soient prises en compte. Si vous utilisez supervisor, il faudra redémarrer le service web de la même manière que présenté ci-dessous. Cependant pour les deux autres services, une seule commande sera nécessaire.

{% tabs %}
{% tab title="Service web" %}
```bash
sudo systemctl restart apache2
```
{% endtab %}

{% tab title="Open-Capture Verifier" %}
```
sudo systemctl restart OCVerifier-worker_CUSTOMID
```
{% endtab %}

{% tab title="Open-Capture Splitter" %}
```
sudo systemctl restart OCSplitter-worker_CUSTOMID
```
{% endtab %}

{% tab title="supervisor" %}
```
sudo supervisorctl restart all
```
{% endtab %}
{% endtabs %}

Dans le cas où le (ou les) worker est totalement down il sera possible de redémarrer totalement le service `rabbitMQ`, la librairie gérant les piles de documents et permettant de les traiter un par un.&#x20;

```bash
rabbitmqctl stop_app
rabbitmqctl start_app
```
