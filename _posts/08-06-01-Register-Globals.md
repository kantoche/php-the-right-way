---
isChild: true
---

## Variables super-globales {#register_globals_title}

**NOTE:** A partir de PHP 5.4.0 la configuration de `register_globals` a été supprimée et ne peut plus être utilisée. Cela est signalé par une alerte dans le cas d'une procédure de mise à jour d'une ancienne application.

Lorsqu'il est activé, le paramètre de configuration `register_globals` permet à différents types de variable (dont notamment `$_POST`, `$_GET` et `$_REQUEST`) d'être disponible au niveau global de votre application. Ce qui peut facilement conduire à des problèmes de sécurité puisque votre application ne peut plus déterminer d'où proviennent les données.

Par exemple : `$_GET['foo']` serait disponible via `$foo`, qui peut outrepasser alors les variables qui n'ont pas été déclarées. Si vous utilisez PHP < 5.4.0 __assurez-vous__ que `register_globals` est à __off__.

* [Register_globals dans le manuel PHP](http://www.php.net/manual/fr/security.globals.php)
