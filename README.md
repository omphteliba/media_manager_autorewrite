MM Autorewrite
========================

Dieses AddOn macht automatisch aus deinen Media Manager URLs schöne URLs (über den OUTPUT_FILTER).
Funktioniert für alle Attribute (src="index.php..", href="index.php...", jedoch nicht für Background-Images). Die Attribute können eingestellt werden. Das `media_manager_srcset` AddOn rewrited in der neuesten Version automatisch. background-images können manuell rewrited werden. (siehe unten)

> index.php?rex_media_type=ImgTypeName&rex_media_file=ImageFileName

wird zu

> images/mediatype/filename.jpg

Es wird automatisch innerhalb von src, href und data-highresmobile gesucht. Es können weitere auf der AddOn Page angegeben werden.

![Screenshot](https://raw.githubusercontent.com/FriendsOfREDAXO/media_manager_autorewrite/assets/screen.png)

Settingspage
------------
Die Settingspage integriert sich als Tab-Reiter innerhalb des AddOns yRewrite.
Innerhalb der Settingspage kann die Base-Einstellung aktiviert oder deaktiviert werden. Des Weiteren kann der Media Manager Expire-Fix zugeschaltet werden, falls deine .htaccess das Ablaufdatum für Mediamanager Medien nicht beeinflussen kann.

Installation
------------
Hinweis: dies ist kein Plugin!

* Release herunterladen und entpacken.
* Ordner umbenennen in `media_manager_autorewrite`.
* In den Addons-Ordner legen: `/redaxo/src/addons`.

Oder den REDAXO-Installer / ZIP-Upload AddOn nutzen!

Manuell
------------
Wenn du z.B. ein inline background-image rewriten willst, musst du das in deiner Ausgabe manuell machen. Anstatt den kompletten String anzugeben, kannst du auch einfach nur folgendes machen

Falls du bereits Redaxo 5.7 nutzt, kannst du auch direkt auf Boardmittel zugreifen, denn der Core liefert jetzt selbst eine Funktion dafür.

```php
<?php
    echo rex_media_manager::getUrl($type, $file, $timestamp = null);
    // $timestamp ist für Cache Busting interessant
```

Siehe: https://github.com/redaxo/redaxo/blob/master/redaxo/src/addons/media_manager/lib/media_manager.php#L388

* Für User mit diesem AddOn und Redaxo < 5.7

```php
<?php
    echo mm_auto::rewrite('dateiname.jpg', 'imagetype');
    // Ausgabe: /media/imagetyp/dateiname.jpg (oder ../images/, abhängig von der BASE-Tag Einstellung)
?>
```

Voraussetzungen
------------

* yrewrite AddOn
* media_manager AddOn

Thanks
----
* Jan Camrda (@jdlx) für das Herz dieses AddOns, die Regular-Expression zum Ersetzen.
* Joachim Dörr für die Settingspage und Hilfe bei der Einrichtung
