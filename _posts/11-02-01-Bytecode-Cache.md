---
isChild: true
---

## Cache de bytecode {#bytecode_cache_title}

Quand un fichier PHP est exécuté, il est d'abord compilé en bytecode (aussi connu sous le nom d'optcode) sous le manteau et, seulement alors, le bytecode est exécuté.
Si un fichier PHP n'est pas modifié, le bytecode restera toujours le même. Cela signifie que l'étape de compilation est un gaspillage de ressources CPU.

C'est ici que le cache de bytecode intervient. Il empèche la compilation redondante en stockant le bytecode en mémoire et en le réutilisant lors d'appels successifs.
Mettre en place un cache de bytecode est une affaire de quelques minutes, et votre application gagnera significativement en rapidité. Il n'y a vraiment aucune raison de ne pas l'utiliser.

Les caches de bytecode les plus populaires sont :

* [APC](http://php.net/manual/en/book.apc.php)
* [XCache](http://xcache.lighttpd.net/)
* [Zend Optimizer+](http://www.zend.com/products/server/) (partie du paquetage de Zend Server)
* [WinCache](http://www.iis.net/download/wincacheforphp) (extension pour MS Windows Server)
