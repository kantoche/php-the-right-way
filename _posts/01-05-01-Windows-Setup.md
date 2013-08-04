---
isChild: true
---

## Installation sous Windows {#windows_setup_title}

PHP est disponibles de différentes façons sous Windows. Vous pouvez [télécharger les fichiers exécutables][php-downloads] et jusqu'à récemment vous pouviez utiliser un programme d'installation '.msi'. Ce type de programme n'est plus désormais supporté et s'est arrêté avec PHP 5.3.0.

Pour l'apprentissage et le développement en local, vous pouvez utiliser le serveur web interne fourni à partir de PHP 5.4 sans vous soucier alors de sa configuration. Si vous préférez un "tout-en-un" qui inclut un serveur web complet ainsi que MySQL, alors des outils tels que les [Web Platform Installer][wpi], 
[Zend Server CE][zsce], [XAMPP][xampp] et [WAMP][wamp] vous aideront à obtenir un environnement de développement rapidement opérationnel sous Windows. Ceci étant dit, les outils utilisés en production sont quelque peu différents, aussi soyez attentifs à ces différences d'environnement si vous êtes amenés à développer sous Windows et à déployer sous Linux.

Si vous avez besoin de faire tourner votre système en production sous Windows, le serveur IIS7 vous procurera la plus grande stabilité et les meilleures performances. Vous pouvez utiliser [phpmanager][phpmanager] (plugin d'une interface graphique pour IIS7) pour faciliter la configuration et la gestion de PHP. IIS7 est fourni avec FastCGI intégré et prêt à l'emploi, il vous suffit juste de configurer PHP comme un gestionnaire. Pour le support et les ressources additionnelles, il existe un [espace dédié sur iis.net][php-iis] pour PHP.

[php-downloads]: http://windows.php.net
[phpmanager]: http://phpmanager.codeplex.com/
[wpi]: http://www.microsoft.com/web/downloads/platform.aspx
[zsce]: http://www.zend.com/en/products/server-ce/
[xampp]: http://www.apachefriends.org/en/xampp.html
[wamp]: http://www.wampserver.com/
[php-iis]: http://php.iis.net/
