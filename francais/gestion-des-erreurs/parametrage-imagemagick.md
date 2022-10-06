# Paramétrage ImageMagick

Dans certains cas il est possible que la conversion PDF vers JPG ne se fait pas complétement. Par exemple, un document PDF de 3 pages ne vous donne qu'une seule page en sortie. Dans ce cas là plusieurs choses peuvent être faites. Dans un premier temps, modifier la compression dans le fichier de config à l'aide de la commande suivante : &#x20;

```
nano /var/www/html/opencapture/instance/config/config_DEFAULT.ini
```

Par défaut cette dernière est à 100, abaissez là à 80, par exemple.

{% code title="config_DEFAULT.ini" %}
```
compressionquality = 80
```
{% endcode %}

Si le problème est toujours présent, il peut être utile de modifier un réglage propre à ImageMagick, la librairie système permettant, entre autre choses, la conversion PDF vers JPG. Vous vous rendrez donc dans le documents à l'aide de cette ligne dans le terminal :&#x20;

```
nano /etc/ImageMagick-6/policy.xml
```

Trouver la ligne ci-dessous afin de modifier la valeur par défaut de `1GiB` en `2GiB`, ou plus si nécessaire. Il faut être en root afin de modifier ce fichier.&#x20;

{% code title="policy.xml" %}
```
  <policy domain="resource" name="disk" value="2GiB"/>
```
{% endcode %}

Une erreur liée à ImageMagick peut se présenter dans les fichiers de log d'**Open-Capture** sous la forme suivante :&#x20;

```
[Open-Capture] [Files.py line 116] 23-03-2022 10:37:24 ERROR Error during WAND conversion : cache resources exhausted `/tmp/magick-4Y6hEmOB8ThLiot7RrMUSnDMkfM9ufgr66' @ error/cache.c/OpenPixelCache/4095
```
