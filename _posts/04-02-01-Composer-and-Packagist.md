---
isChild: true
---

## Composer et Packagist {#composer_and_packagist_title}

Composer est un gestionnaire de dépendances **génial** pour PHP. Listez les dépendances de votre projet dans un fichier `composer.json` et, au moyen de quelques commandes simples, Composer téléchargera automatiquement les dépendances de votre projet et configurera leur chargement automatique pour vous.

Il existe déjà de nombreuses bibliothèques PHP compatibles avec Composer, prêtes à l'emploi dans vos projets. Ces "paquetages" sont listés sur [Packagist][1], le dépôt officiel des bibliothèques PHP compatibles avec Composer.

### Comment installer Composer

Vous pouvez installer Composer localement (dans votre dossier de travail courant, bien que ce ne soit plus recommandé) ou globalement (e.g. /usr/local/bin). Supposons que vous souhaitiez installer Composer localement. A partir du dossier racine de votre projet :

    curl -s https://getcomposer.org/installer | php

Cette commande téléchargera `composer.phar` (une archive binaire PHP). Vous pouvez la lancer avec `php` pour gérer les dépendances de votre projet. <strong>Remarque importante : </strong> si vous aiguillez directement un code téléchargé vers un interpréteur, prenez soin de consulter ce code en ligne  pour vous assurer de son innocuité.

### Comment installer Composer (manuellement)

Installer Composer manuellement est une technique avancée; cependant, il y a de nombreuses raisons qui peuvent pousser un développeur à préferer cette méthode à la procédure d'installation interactive. L'installation interactive vérifie votre configuration PHP pour s'assurer que :

- une version adéquate de PHP est utilisée
- les fichiers `.phar` peuvent être exécutés correctement
- les permissions de certains dossiers sont suffisantes
- certaines extensions qui posent problème ne sont pas chargées
- certains paramètres de `php.ini` sont configurés

Puisqu'une installation manuelle ne réalise aucune de ces vérifications, vous devez décider si le compromis en vaut la peine. A cet effet, voici comment obtenir Composer manuellement :

    curl -s https://getcomposer.org/composer.phar -o $HOME/local/bin/composer
    chmod +x $HOME/local/bin/composer

Le chemin `$HOME/local/bin` (ou un dossier de votre choix) devrait se trouver dans votre variable d'environnement `$PATH`. Ceci rendra disponible la commande `composer`.

Lorsque la documentation signale de lancer Composer avec `php composer.phar install`, vous pouvez lui substituer la ligne suivante :

    composer install

### Comment définir et installer les dépendances

Composer garde la trace des dépendances de votre projet dans un fichier appelé `composer.json`. Vous pouvez le gérer à la main si vous le souhaitez, ou bien utiliser Composer lui-même. La commande `php composer.phar require` ajoute une dépendance de projet et si vous n'avez pas de fichier `composer.json`, il sera créé. Voici un exemple de commande qui ajoute [Twig][2] en tant que dépendance de votre projet. Lancez-la dans le dossier racine de votre projet où vous avez téléchargé `composer.phar` :

	php composer.phar require twig/twig:~1.8

Alternativement la commande `php composer.phar init` vous guidera à travers la création d'un fichier `composer.json` complet pour votre projet. Autre façon de faire, une fois que vous avez créé votre fichier `composer.json`, vous pouvez demander à Composer de télécharger et d'installer vos dépendances dans le dossier `vendors/`. Cela s'applique également aux projets que vous avez téléchargés et qui disposent déjà d'un fichier `composer.json` :

    php composer.phar install

Ensuite, ajoutez cette ligne au fichier PHP de lancement de votre application; elle signalera à PHP d'utiliser le chargeur automatique de Composer pour les dépendances de votre projet.

{% highlight php %}
<?php
require 'vendor/autoload.php';
{% endhighlight %}

Désormais vous pouvez utiliser les dépendances de votre projet, et elles seront chargées automatiquement à la demande.

### Mettre à jour vos dépendances

Composer crée un fichier appelé `composer.lock` qui enregistre la version exacte de chaque paquetage qu'il a téléchargé lors du premier lancement de `php composer.phar install`. Si vous partagez votre projet avec d'autres développeurs et que le fichier `composer.lock` fait partie de votre distribution, alors ils obtiendront les mêmes versions que vous à l'exécution de `php composer.phar install`. Pour mettre à jour vos dépendances, lancez `php composer.phar update`.

Cela est des plus utile lorsque vous définissez la flexibilité des exigences d'une version. Par exemple, une exigence de version correspondant à ~1.8 signifie "toute version supérieure à 1.8.0, mais inférieure à 2.0.x-dev". Vous pouvez aussi utiliser le caractère de remplacement `*` comme dans `1.8.*`. Maintenant la commande de Composer `php composer.phar update` mettra à jour toutes vos dépendances avec la version la plus récente qui convient aux restrictions que vous avez définies.

### Vérifier les problèmes de sécurité de vos dépendances

Le [Security Advisories Checker][3] est un service web et un outil en ligne de commande qui examinent votre fichier `composer.lock` et vous signalent la nécessité de mettre à jour si besoin l'une de vos dépendances.

* [En savoir plus sur Composer][4]

[1]: http://packagist.org/
[2]: http://twig.sensiolabs.org
[3]: https://security.sensiolabs.org/
[4]: http://getcomposer.org/doc/00-intro.md

