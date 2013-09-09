---
isChild: true
---

## Rapport d'erreur {#error_reporting_title}

Tracer les erreurs est chose utile pour déceler les problèmes dans votre application, mais cela peut aussi exposer des informations sur la structure de votre application au reste du monde. C'est pourquoi, afin de protéger votre application des risques éventuels encourus par la publication de ces messages, vous devez configurer votre serveur différemment en développement et en production (live).

### Développement

Pour montrer toutes les erreurs possibles pendant la phase de <strong>développement</strong>, configurez les paramètres suivants dans votre `php.ini`:

    display_errors = On
    display_startup_errors = On
    error_reporting = -1
    log_errors = On

> Fixer la valeur à `-1` montrera toutes les erreurs possibles, même si de nouveaux niveaux et de nouvelles constantes sont ajoutés dans des versions ultérieures de PHP. La constante `E_ALL` se comporte également de la même façon à partir de PHP 5.4. - [php.net](http://php.net/manual/fr/function.error-reporting.php)

La constante de niveau d'erreur `E_STRICT` a été introduite en 5.3.0 et ne faisait pas alors partie intégrante de `E_ALL`, ce qu'elle est toutefois devenue en 5.4.0. Qu'est-ce à dire ? Cela signifie que dans la version 5.3 vous devez utiliser soit `-1` soit `E_ALL | E_STRICT` afin de rapporter toutes les erreurs possibles.

**Rapporter toutes les erreurs possibles en fonction de la version de PHP**

* &lt; 5.3 `-1` or `E_ALL`
* &nbsp; 5.3 `-1` or `E_ALL | E_STRICT`
* &gt; 5.3 `-1` or `E_ALL`

### Production

Pour masquer les erreurs dans votre environnement de <strong>production</strong>, configurez votre `php.ini` comme suit :

    display_errors = Off
    display_startup_errors = Off
    error_reporting = E_ALL
    log_errors = On

Avec ces paramètres en production, les erreurs seront toujours enregistrées dans les fichiers d'erreurs du serveur web, mais elles ne seront plus exposées aux utilisateurs. Pour plus d'informations sur ces paramètres, consultez le manuel PHP :

* [error_reporting](http://php.net/manual/errorfunc.configuration.php#ini.error-reporting)
* [display_errors](http://php.net/manual/errorfunc.configuration.php#ini.display-errors)
* [display_startup_errors](http://php.net/manual/errorfunc.configuration.php#ini.display-startup-errors)
* [log_errors](http://php.net/manual/errorfunc.configuration.php#ini.log-errors)
