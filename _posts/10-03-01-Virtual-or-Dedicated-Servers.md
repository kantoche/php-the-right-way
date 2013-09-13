---
isChild: true
---

## Serveurs virtuels ou dédiés {#virtual_or_dedicated_servers_title}

Si vous êtes à l'aise avec l'administration système ou si vous êtes intéressé de l'apprendre, les serveurs virtuels ou dédiés vous donnent un contrôle complet de l'environnement de production de votre application.

### nginx et PHP-FPM

PHP, via le gestionnaire de processus FastCGI (FPM) natif de PHP, s'intégre vraiment bien avec [nginx](http://nginx.org), qui est un serveur web léger et à haute performance. Il utilise moins de mémoire qu'Apache et peut mieux gérer un très grand nombre de requêtes concurrentes. C'est particulièrement important pour des serveurs virtuels qui ne disposent pas de beaucoup de mémoire en partage.

* [En savoir plus sur nginx](http://nginx.org)
* [En savoir plus sur PHP-FPM](http://php.net/manual/fr/install.fpm.php)
* [En savoir plus sur la configuration sécurisée de nginx et PHP-FPM](https://nealpoole.com/blog/2011/04/setting-up-php-fastcgi-and-nginx-dont-trust-the-tutorials-check-your-configuration/)

### Apache et PHP

PHP et Apache partagent une longue histoire. Apache est extrèmement configurable et dispose de nombreux [modules](http://httpd.apache.org/docs/2.4/mod/) pour étendre ses fonctionnalités. C'est un choix populaire pour des serveurs mutualisés et pour une mise en place facile de cadres de travail PHP et d'applications open source telles que WordPress. Malheureusement, Apache utilise plus de ressources par défaut que nginx et ne peut pas gérer autant de visiteurs en même temps.

Apache a plusieurs configurations possibles pour faire fonctionner PHP. La plus commune et la plus facile à mettre en place est le [prefork MPM](http://httpd.apache.org/docs/2.4/mod/prefork.html) avec mod_php5. Bien qu'il ne soit pas le plus efficace du point de vue de la mémoire, il est le plus simple à utiliser ou pour débuter. C'est probablement le meilleur choix si vous ne souhaitez pas vous plonger à fond dans les méandres de l'administration serveur. Notez que si vous utilisez mod_php5, vous DEVEZ utiliser le prefork MPM.

Alternativement, si vous voulez profiter d'une meilleure performance et d'une meilleure stabilité avec Apache, alors vous pouvez tirer avantage du même système FPM que nginx et lancer le [worker MPM](http://httpd.apache.org/docs/2.4/mod/worker.html) ou [event MPM](http://httpd.apache.org/docs/2.4/mod/event.html) avec mod_fastcgi ou mod_fcgid. Cette configuration sera largement plus efficace du point de vue mémoire et plus rapide, mais elle requiert plus de travail pour sa mise en place.

* [En savoir plus sur Apache](http://httpd.apache.org/)
* [En savoir plus sur Multi-Processing Modules](http://httpd.apache.org/docs/2.4/mod/mpm_common.html)
* [En savoir plus sur mod_fastcgi](http://www.fastcgi.com/mod_fastcgi/docs/mod_fastcgi.html)
* [En savoir plus sur mod_fcgid](http://httpd.apache.org/mod_fcgid/)
