---
isChild: true
---

## Paradigmes de la programmation {#programming_paradigms_title}

PHP est un langage flexible et dynamique qui supporte des techniques de programmation variées. Il a énormément évolué au fil des ans, s'entourant notablement d'un solide modèle orienté objet avec PHP 5.0 (2004), de fonctions anonymes et d'espaces de nom avec PHP 5.3 (2009), et des traits avec PHP 5.4 (2012).

### Programmation orientée objet

PHP dispose d'un ensemble très complet de fonctionnalités/caractéristiques de la programmation orientée objet qui inclut le support des classes, les classes abtraites, les interfaces, l'héritage, les constructeurs, le clonage, les exceptions et bien plus encore.

* [A propos de PHP orienté objet][oop]
* [A propos des Traits][traits]

### Programmation fonctionnelle

PHP supporte les fonctions de première classe, ce qui signifie qu'une fonction peut être assignée à une variable. Qu'il s'agisse de fonctions internes ou bien de fonctions définies par l'utilisateur, elles peuvent être référencées par une variable et invoquées dynamiquement. Les fonctions peuvent être passées comme argument à d'autres fonctions (particularité appelée fonctions de plus haut niveau) et elles peuvent retourner d'autres fonctions.

La récursivité, une fonctionnalité qui permet à une fonction de s'appeler elle-même est supportée par le langage, bien que la plupart du code PHP mette l'accent sur l'itération.

De nouvelles fonctions anonymes (avec le support des clôtures) sont disponibles depuis PHP 5.3 (2009).

PHP 5.4 a ajouté la capacité de lier les clôtures à la portée d'un objet et a amélioré de ce fait le support des fonctions de rappel de telle manière qu'elles puissent être interchangeables avec les fonctions anonymes dans la plupart des cas.

* Poursuivre la lecture à propos de la [programmation fonctionnelle en PHP](/pages/Functional-Programming.html)
* [A propos des fonctions anonymes][anonymous-functions]
* [A propos de la classe Closure][closure-class]
* [Plus de détails dans la RFC Closures][closures-rfc]
* [A propos des fonctions de rappel][callables]
* [A propos de l'invocation dynamique de fonctions au moyen de `call_user_func_array`][call-user-func-array]

### Metaprogrammation

PHP supporte des formes variées de métaprogrammation au travers de mécanismes comme la l'API de Reflection et les méthodes magiques. Il y a de nombreuses méthodes magiques disponibles comme `__get()`, `__set()`, `__clone()`, `__toString()`, `__invoke()`, etc. qui permettent aux développeurs d'accéder au comportement d'une classe. Les développeurs Ruby disent souvent qu'il manque une `method_missing` en PHP, mais celle-ci reste disponible à travers les méthodes `__call()` et `__callStatic()`.

* [A propos des méthodes magiques][magic-methods]
* [A propos de la Reflection][reflection]

[namespaces]: http://php.net/manual/fr/language.namespaces.php
[overloading]: http://php.net/manual/fr/language.oop5.overloading.php
[oop]: http://www.php.net/manual/fr/language.oop5.php
[anonymous-functions]: http://www.php.net/manual/fr/functions.anonymous.php
[closure-class]: http://php.net/manual/fr/class.closure.php
[callables]: http://php.net/manual/fr/language.types.callable.php
[magic-methods]: http://php.net/manual/fr/language.oop5.magic.php
[reflection]: http://www.php.net/manual/fr/intro.reflection.php
[traits]: http://www.php.net/traits
[call-user-func-array]: http://php.net/manual/fr/function.call-user-func-array.php
[closures-rfc]: https://wiki.php.net/rfc/closures
