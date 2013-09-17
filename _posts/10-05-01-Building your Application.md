---
isChild: true
---

## Construire et déployer votre application {#build_title}

Si vous vous retrouverez à faire manuellement des modifications au schéma de la base de données ou à lancer manuellement vos tests avant de mettre à jour vos fichiers (manuellement), réfléchissez-y à deux fois ! Avec chaque opération manuelle nécessitée par le déploiement d'une nouvelle version de votre application, les chances de provoquer potentiellement des erreurs fatales s'accroissent. Que vous soyez occupé par une simple mise à jour, un processus d'élaboration complet ou même une stratégie d'intégration continue, une [solution d'automatisation](http://en.wikipedia.org/wiki/Build_automation) est votre amie.

Parmi les tâches que vous pourriez vouloir automatiser, on trouve :

* Gestion des dépendances
* Compilation, minimisation de vos ressources
* Lancement de test
* Création de documentation
* Création de paquetage
* Déploiement


### Moteurs de production

Les moteurs de production peuvent décrits comme une collection de scripts qui gèrent différentes tâches courantes de déploiement logiciel. Le moteur de production ne fait pas partie de votre programme, il agit sur votre programme de l'extérieur.

Il existe de nombreux outils open source disponibles pour vous aider à mettre en place une automatisation, certains sont écrits en PHP et d'autres non. Cela ne devrait pas vous retenir de les utiliser, s'ils conviennent mieux à un besoin spécifique. Voici quelques exemples :

[Phing](http://www.phing.info/) est la façon la plus simple de faire ses premiers pas avec le déploiement automatique dans le monde PHP. Avec Phing vous pouvez contrôler la création de votre paquetage, son déploiement ou votre procédure de test au moyen d'un simple fichier de construction XML. Phing (qui est basé sur [Apache Ant](http://ant.apache.org/)) fournit une large palette de tâches habituellement requises pour installer ou mettre à jour une application web et peut être enrichi de tâches additionnelles personnalisées, écrites en PHP.

[Capistrano](https://github.com/capistrano/capistrano/wiki) est un système pour *des programmeurs de niveau intermédiaire ou avancé* afin d'exécuter des commandes de façon structurée et répétée sur une ou plusieurs machines distantes. Bien qu'il soit préconfiguré pour le déploiement d'applications Ruby on Rails, on peut **déployer avec succès des systèmes PHP** grâce à lui. Une utilisation réussie de Capistrano repose sur une bonne connaissance de Ruby et de Rake.

L'article du blog de Dave Gardner, [PHP Deployment with Capistrano](http://www.davegardner.me.uk/blog/2012/02/13/php-deployment-with-capistrano/) est un bon point de départ pour les développeurs PHP intéressés par Capistrano.

[Chef](http://www.opscode.com/chef/) est plus qu'un cadre de travail de déploiement, c'est un cadre de travail Ruby très puissant basé sur un système d'intégration qui, en plus de déployer votre application, peut construire votre environnement serveur complet ou vos machines virtuelles.

Ressources à propos de Chef pour les développeurs PHP :

* [Une série de trois articles sur le déploiement d'une application LAMP avec Chef, Vagrant et EC2](http://www.jasongrimes.org/2012/06/managing-lamp-environments-with-chef-vagrant-and-ec2-1-of-3/)
* [Chef Cookbook à propos de l'installation et de la configuration de PHP 5.3 et du système de gestion de paquetages PEAR](https://github.com/opscode-cookbooks/php)

Lectures supplémentaires :

* [Automatiser votre projet avec Apache Ant](http://net.tutsplus.com/tutorials/other/automate-your-projects-with-apache-ant/)
* [Maven](http://maven.apache.org/), un moteur de production basé sur Ant et [comment l'utiliser avec PHP](http://www.php-maven.org/)

### Intégration continue

> L'intégration continue est une pratique de développement logiciel où les membres d'une équipe intègre leur travail fréquemment, 
> sur la base d'une intégration au moins quotidienne pour chacune des personnes — ce qui conduit à de multiples intégrations par jour. De nombreuses équipes considèrent que cette 
> approche favorise grandement la réduction des problèmes d'intégration et permet à l'équipe de développer un logiciel solide plus 
> rapidement.

*-- Martin Fowler*

Il y a différentes manières de mettre en place une intégration continue pour PHP. Récemment, [Travis CI](https://travis-ci.org/) a fait beaucoup pour que l'intégration continue devienne une réalité même pour les petits projets. Travis CI est un service d'hébergement d'intégration continue pour la communauté open source. Il est intégré à GitHub et offre un support de premier choix pour de nombreux langages dont PHP.

Lectures supplémentaires :

* [Intégration continue avec Jenkins](http://jenkins-ci.org/)
* [Intégration continue avec PHPCI](http://www.phptesting.org/)
* [Intégration continue avec Teamcity](http://www.jetbrains.com/teamcity/)
