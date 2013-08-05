# Conventions de codage {#code_style_guide_title}

La communauté PHP est vaste et diverse, composée d'innombrables bibliothèques, cadres de travail et composants. Il est fréquent que des développeurs PHP en choisissent plusieurs et les combinent dans un unique projet. Il est important que le code PHP adhère (aussi étroitement que possible) à un style commun de codage pour faciliter le travail des développeurs lorsqu'ils intègrent et font communiquer ces différentes bibliothèques dans leurs projets.

Le [Framework Interop Group][fig] a proposé et approuvé une série de recommandations de style, connue sous les noms de [PSR-0][psr0], [PSR-1][psr1] et [PSR-2][psr2]. Ne vous laissez pas perturber par ces drôles de noms, ces recommandations sont principalement un ensemble de règles en cours d'adoption par des projets tels que Drupal, Zend, Symfony, CakePHP, phpBB, AWS SDK, FuelPHP, Lithium, etc. Vous pouvez les utiliser pour vos propres projets, ou poursuivre avec votre propre style personnel.

Dans l'idéal, vous devriez écrire un code PHP qui adhère à un standard connu. Ce pourrait être n'importe quelle combinaison de PSR, ou l'un des standards de codage proposés par PEAR ou Zend. Ainsi, d'autres développeurs peuvent appréhender et réutiliser votre code facilement, et les applications qui en intègrent les composants peuvent gagner en homogénéité même si elles font appel à de nombreux codes tiers. 

* [Read about PSR-0][psr0]
* [Read about PSR-1][psr1]
* [Read about PSR-2][psr2]
* [Read about PEAR Coding Standards][pear-cs]
* [Read about Zend Coding Standards][zend-cs]

Vous pouvez utiliser [PHP_CodeSniffer][phpcs] pour vérifier la conformité d'un code par rapport à l'une de ces recommandations, et certains éditeurs de texte disposent de plugins pour une analyse en temps réel, comme [Sublime Text 2][st-cs]. 

Utilisez le [PHP Coding Standards Fixer][phpcsfixer] de Fabien Potencier pour modifier automatiquement la syntaxe de votre code afin qu'elle se conforme à ces standards, vous épargnant ainsi la tâche de corriger chaque problème à la main.

Il est préférable d'utiliser l'anglais pour les noms de symbole et l'infrastructure du code. Les commentaires peuvent être écrits dans n'importe quelle langue facilement accessible pour toutes les parties présentes et à venir amenées à travailler sur la base de ce code.

[fig]: http://www.php-fig.org/
[psr0]: https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-0.md
[psr1]: https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-1-basic-coding-standard.md
[psr2]: https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-2-coding-style-guide.md
[psr3]: https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-3-logger-interface.md
[pear-cs]: http://pear.php.net/manual/en/standards.php
[zend-cs]: http://framework.zend.com/wiki/display/ZFDEV2/Coding+Standards
[phpcs]: http://pear.php.net/package/PHP_CodeSniffer/
[st-cs]: https://github.com/benmatselby/sublime-phpcs
[phpcsfixer]: http://cs.sensiolabs.org/
