---
isChild: true
---

## Cache d'objet {#object_caching_title}

Il y a des situations où il peut être bénéfique de mettre en cache des objets individuels dans votre code, tels que ceux dont les données sont coûteuses à obtenir ou les appels à la base de données dont il est peu probable que le résultat change. Vous pouvez utiliser un cache d'objet pour conserver ces données en mémoire pour un accès ultérieur très rapide. Si vous sauvegardez ces éléments dans un dépôt de données après extraction et que vous les récupérez directement à partir du cache lors des requêtes suivantes, vous pouvez tout à la fois améliorer vos gains de performance et réduire la charge de vos serveurs de base de données.

Beaucoup de solutions de cache de bytecode vous laisse également mettre en cache des données personnalisées, donc une bonne raison supplémentaire d'en tirer avantage. APC, XCache et WinCache fournissent tout trois une API pour sauvegarder les données de votre code PHP dans leur cache en mémoire.

Les systèmes de cache d'objet les plus communément employés sont APC et memcached. APC est un excellent choix pour la mise en cache d'objet, il inclut une API pour l'ajout de vos propres données à son cache en mémoire et il est d'une grande facilité à installer et à utiliser. La seule vraie limitation d'APC est qu'il est lié au serveur sur lequel il est installé. Memcached est à l'inverse installé comme un service séparé et peut être accédé depuis le réseau, ce qui signifie que vous pouvez stocker des objets dans un dépôt de données ultra-rapide et centralisé dans lequel de nombreux systèmes différents peuvent venir puiser.

Notez que lorsque vous lancez PHP comme une application (Fast-)CGI sur votre serveur web, chaque processus PHP aura son propre cache, c'est-à-dire que les données APC ne sont pas partagées entre vos processus actifs. Dans ce cas, vous pourriez vouloir envisager à la place l'utilisation de memcached, puisqu'il n'est pas lié aux processus PHP.

Dans une configuration en réseau, APC dépassera généralement memcached en terme de rapidité d'accès, mais memcached sera capable d'augmenter plus rapidement et davantage. Si vous ne prévoyez pas de faire tourner votre application sur de multiples serveurs, ou si vous n'avez pas besoin des fonctionnalités supplémentaires qu'offre memcached, alors APC est probablement votre meilleure option pour la mise en cache d'objet.

Exemple d'utilisation d'APC :

{% highlight php %}
<?php
// check if there is data saved as 'expensive_data' in cache
$data = apc_fetch('expensive_data');
if ($data === false) {
    // data is not in cache; save result of expensive call for later use
    apc_add('expensive_data', $data = get_expensive_data());
}

print_r($data);
{% endhighlight %}

En savoir plus sur les systèmes de cache d'objet les plus populaires :

* [APC Functions](http://php.net/manual/en/ref.apc.php)
* [Memcached](http://memcached.org/)
* [Redis](http://redis.io/)
* [XCache APIs](http://xcache.lighttpd.net/wiki/XcacheApi)
* [WinCache Functions](http://www.php.net/manual/en/ref.wincache.php)
