---
title: Bases de données
---

# Bases de données {#databases_title}

A de nombreuses reprises votre code PHP utilisera une base de données pour assurer la persistance de l'information. Vous avez quelques options pour vous connecter et interagir avec votre base de données. L'option recommandée _jusqu'à PHP 5.1.0_ était l'utilisation des pilotes intégrés tels que [mysql][mysql], [mysqli][mysqli], [pgsql][pgsql], etc.

Les pilotes intégrés sont formidables si vous utilisez seulement UNE base de données dans votre application, mais si, par exemple, vous avez besoin de MySQL et d'un peu de MSSQL, ou d'une connexion à une base Oracle, alors vous ne serez pas en mesure d'utiliser les mêmes pilotes. Vous aurez besoin d'apprendre une nouvelle API propriétaire pour chaque base de données &mdash; et cela peut tourner à l'absurde.

En guise de note supplémentaire sur les pilotes intégrés, l'extension mysql pour PHP n'est plus désormais en développement actif, et son statut officiel depuis PHP 5.4.0 est "Long term deprecation". Cela signifie qu'elle sera supprimée lors d'une prochaine mise à jour, et qu'elle pourrait très bien être retirée avec PHP 5.6 (ou n'importe quelle version qui viendra après la 5.5.) Si vous utilisez `mysql_connect()` et `mysql_query()` dans vos applications, alors vous serez confrontés à une réécriture de code un peu plus tard, si bien que la meilleure option est de prévoir dès à présent dans votre planning de développement le remplacement de mysql par mysqli ou PDO dans vos applications, pour éviter de tomber dans l'urgence au dernier moment. _Si vous partez de zéro, vous devez absolument éviter l'extension mysql : utilisez l'[extension MySQLi][mysqli], ou bien PDO._

* [PHP : choisir une API pour MySQL](http://php.net/manual/en/mysqlinfo.api.choosing.php)

## PDO

PDO est une bibliothèque d'abstraction de connexion aux bases de données &mdash; intégrée à PHP depuis la version 5.1.0 &mdash; qui fournit une interface commune pour communiquer avec de nombreuses bases différentes. PDO ne traduira pas vos requêtes SQL ni n'émulera les fonctionnalités manquantes; Elle est purement dédiée à la connexion avec des types multiples de bases de données au moyen de la même API.

Plus important, `PDO` vous permet d'injecter en toute sécurité des données étrangères (e.g. IDs) dans vos requêtes SQL sans vous soucier des attaques d'injection SQL. Cela est possible grâce aux expressions PDO et aux paramètres liés.

Imaginons qu'un script PHP reçoive un ID numérique comme paramètre de requête. Cet ID devrait être utilisé pour récupérer un enregistrement dans la base. Voici la `mauvaise` manière de procéder :

{% highlight php %}
<?php
$pdo = new PDO('sqlite:users.db');
$pdo->query("SELECT name FROM users WHERE id = " . $_GET['id']); // <-- NON !
{% endhighlight %}

Ce code est horrible. Vous insérez un paramètre de requête brut dans votre requête SQL. Vous allez vous faire pirater en un battement de paupière. Imaginez simplement qu'un pirate transmette un paramètre `id` factice en appelant un URL comme `http://domain.com/?id=1%3BDELETE+FROM+users`. La variable `$_GET['id']` se voit alors attribuer la valeur `1;DELETE FROM users` dont le résultat est la suppression de tous vos utilisateurs ! A la place, vous devez nettoyer la donnée ID au moyen des paramètres liés de PDO. 

{% highlight php %}
<?php
$pdo = new PDO('sqlite:users.db');
$stmt = $pdo->prepare('SELECT name FROM users WHERE id = :id');
$stmt->bindParam(':id', $_GET['id'], PDO::PARAM_INT); //<-- nettoyage automatique par PDO
$stmt->execute();
{% endhighlight %}

Voilà le code correct. Il utilise un paramètre lié dans une expression PDO. It uses a bound parameter on a PDO statement. La donnée ID étrangère est échappée avant son introduction dans la base de données, prévenant ainsi toute attaque potentielle d'injection SQL.

* [Learn about PDO][1]

You should also be aware that database connections use up resources and it was not unheard-of to have resources
exhausted if connections were not implicitly closed, however this was more common in other languages. Using PDO you
can implicitly close the connection by destroying the object by ensuring all remaining references to it are deleted,
i.e. set to NULL.  If you don't do this explicitly, PHP will automatically close the connection when your script ends -
unless of course you are using persistent connections.

* [A propos des connexions PDO][5]

## Couches d'abstraction

De nombreux cadres de travail fournissent leur propre couche d'abstraction qui peut reposer ou non au-desssus de PDO. Elles émulent souvent des fonctionnalités disponibles pour un système de base de données et manquantes pour un autre, en encapsulant vos requêtes dans des méthodes PHP, ce qui offre une réelle abstraction de la base de données. Cela occasionne bien entendu un peu de surcharge, mais si vous réalisez une application portable qui a besoin de fonctionner avec MySQL, PostgreSQL et SQLite, alors cette petite surcharge vaut bien le bénéfice d'un code propre.

Certaines couches d'abstraction ont été construites en utilisant le standard des espaces de nom PSR-0 et elles peuvent donc être installées dans n'importe quelle application de votre choix :

* [Aura SQL][6]
* [Doctrine2 DBAL][2]
* [ZF2 Db][4]
* [ZF1 Db][3]

[1]: http://www.php.net/manual/en/book.pdo.php
[2]: http://www.doctrine-project.org/projects/dbal.html
[3]: http://framework.zend.com/manual/en/zend.db.html
[4]: http://packages.zendframework.com/docs/latest/manual/en/index.html#zend-db
[5]: http://php.net/manual/en/pdo.connections.php
[6]: https://github.com/auraphp/Aura.Sql

[mysql]: http://php.net/mysql
[mysqli]: http://php.net/mysqli
[pgsql]: http://php.net/pgsql
