---
title: Databases
---

# Bases de données {#databases_title}

A de nombreuses reprises votre code PHP utilisera une base de données pour assurer la persistance de l'information. Vous avez quelques options pour vous connecter et interagir avec votre base de données. L'option recommandée _jusqu'à PHP 5.1.0_ était l'utilisation des pilotes intégrés tels que [mysql][mysql], [mysqli][mysqli], [pgsql][pgsql], etc.

Les pilotes intégrés sont formidables si vous utilisez seulement UNE base de données dans votre application, mais si, par exemple, vous avez besoin de MySQL et d'un peu de MSSQL, ou d'une connexion à une base Oracle, alors vous ne serez pas en mesure d'utiliser les mêmes pilotes. Vous aurez besoin d'apprendre une nouvelle API propriétaire pour chaque base de données &mdash; et cela peut tourner à l'absurde.

En guise de note supplémentaire sur les pilotes intégrés, l'extension mysql pour PHP n'est plus désormais en développement actif, et son statut officiel depuis PHP 5.4.0 est "Long term deprecation". Cela signifie qu'elle sera supprimée lors d'une prochaine mise à jour, et qu'elle pourrait très bien être retirée avec PHP 5.6 (ou n'importe quelle version qui viendra après la 5.5.) Si vous utilisez `mysql_connect()` et `mysql_query()` dans vos applications, alors vous serez confrontés à une réécriture de code un peu plus tard, si bien que la meilleure option est de prévoir dès à présent dans votre planning de développement le remplacement de mysql par mysqli ou PDO dans vos applications, pour éviter de tomber dans l'urgence au dernier moment. _Si vous partez de zéro, vous devez absolument éviter l'extension mysql : utilisez l'[extension MySQLi][mysqli], ou bien PDO._

* [PHP : choisir une API pour MySQL](http://php.net/manual/en/mysqlinfo.api.choosing.php)

## PDO

PDO is a database connection abstraction library &mdash;  built into PHP since 5.1.0 &mdash; that provides a common interface to talk with
many different databases. PDO will not translate your SQL queries or emulate missing features; it is purely for connecting to multiple types
of database with the same API.

More importantly, `PDO` allows you to safely inject foreign input (e.g. IDs) into your SQL queries without worrying about database SQL injection attacks.
This is possible using PDO statements and bound parameters.

Let's assume a PHP script receives a numeric ID as a query parameter. This ID should be used to fetch a user record from a database. This is the `wrong`
way to do this:

{% highlight php %}
<?php
$pdo = new PDO('sqlite:users.db');
$pdo->query("SELECT name FROM users WHERE id = " . $_GET['id']); // <-- NO!
{% endhighlight %}

This is terrible code. You are inserting a raw query parameter into a SQL query. This will get you hacked in a
heartbeat. Just imagine if a hacker passes in an inventive `id` parameter by calling a URL like
`http://domain.com/?id=1%3BDELETE+FROM+users`.  This will set the `$_GET['id']` variable to `1;DELETE FROM users`
which will delete all of your users! Instead, you should sanitize the ID input using PDO bound parameters.

{% highlight php %}
<?php
$pdo = new PDO('sqlite:users.db');
$stmt = $pdo->prepare('SELECT name FROM users WHERE id = :id');
$stmt->bindParam(':id', $_GET['id'], PDO::PARAM_INT); //<-- Automatically sanitized by PDO
$stmt->execute();
{% endhighlight %}

This is correct code. It uses a bound parameter on a PDO statement. This escapes the foreign input ID before it is introduced to the
database preventing potential SQL injection attacks.

* [Learn about PDO][1]

You should also be aware that database connections use up resources and it was not unheard-of to have resources
exhausted if connections were not implicitly closed, however this was more common in other languages. Using PDO you
can implicitly close the connection by destroying the object by ensuring all remaining references to it are deleted,
i.e. set to NULL.  If you don't do this explicitly, PHP will automatically close the connection when your script ends -
unless of course you are using persistent connections.

* [Learn about PDO connections][5]

## Abstraction Layers

Many frameworks provide their own abstraction layer which may or may not sit on top of PDO.  These will often emulate features for
one database system that another is missing from another by wrapping your queries in PHP methods, giving you actual database abstraction.
This will of course add a little overhead, but if you are building a portable application that needs to work with MySQL, PostgreSQL and
SQLite then a little overhead will be worth it the sake of code cleanliness.

Some abstraction layers have been built using the PSR-0 namespace standard so can be installed in any application you like:

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
