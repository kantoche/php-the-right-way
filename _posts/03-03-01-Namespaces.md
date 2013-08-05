---
isChild: true
---

## Espaces de nom {#namespaces_title}

Comme mentionné ci-dessus, la communauté PHP compte de nombreux développeurs, producteurs de codes. has a lot of developers creating lots of code. Cela signifie qu'une bibliothèque de code PHP peut utiliser le même nom de classe qu'une autre bibliothèque. Quand les deux bibliothèques sont utilisées dans le même espace de nom, elles entrent en collision et posent problème.

_Les espaces de noms_ résolvent ce problème. Comme il est décrit dans le manuel de référence PHP, les espaces de nom peuvent être comparés, dans un système de fichiers, aux dossiers qui _donnent un nom_ aux fichiers; deux fichiers avec le même nom peuvent co-exister dans deux dossiers distincts. De la même façon, deux classes PHP avec le même nom peuvent co-exister dans deux espaces de nom PHP distincts. C'est aussi simple que cela.

Il est important pour vous d'attribuer un espace de nom à votre code afin qu'il puisse être utilisé par d'autres développeurs sans crainte de collision avec d'autres bibliothèques.

Il est recommandé d'utiliser les espaces de nom tel qu'indiqué dans [PSR-0][psr0], qui vise à fournir un standard d'usage des fichier, classe et espace de nom pour permettre un code prêt à l'emploi.

* [A propos des espaces de nom][namespaces]
* [A propos de PSR-0][psr0]

[namespaces]: http://php.net/manual/fr/language.namespaces.php
[psr0]: https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-0.md
