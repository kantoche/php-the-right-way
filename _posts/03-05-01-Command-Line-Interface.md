---
isChild: true
---

## Interface de ligne de commande {#command_line_interface_title}

PHP a été créé au départ pour écrire des applications web, mais il est aussi utile pour les programmes de script de l'interface de ligne de commande (CLI).Les programmes PHP en ligne de commande peuvent vous aider à automatiser des tâches communes telles que le test, le déploiement, et l'administration d'applications.

Les programmes PHP CLI sont puissants parce que vous pouvez utiliser directement le code de votre application sans avoir besoin de créer et de sécuriser une interface utilisateur graphique pour cela. Assurez-vous juste de ne pas déposer vos scripts PHP CLI à la racine publique de votre serveur web !

Essayez d'exécuter PHP à partir de la ligne de commande :

{% highlight bash %}
> php -i
{% endhighlight %}

L'option `-i` affichera votre configuration PHP tout comme la fonction [`phpinfo`][phpinfo]. 

L'option `-a` fournit un shell interactif, similaire à l'IRB de ruby ou au shell interactif de Python. Il y a également de nombreuses autres [options de ligne de commande][cli-options] utiles.

Ecrivons un simple programme CLI "Hello, $name". Pour le tester, créez un fichier nommé `hello.php`, comme ci-dessous.

{% highlight php %}
<?php
if ($argc != 2) {
    echo "Usage: php hello.php [name].\n";
    exit(1);
}
$name = $argv[1];
echo "Hello, $name\n";
{% endhighlight %}

PHP met en place deux variables spéciales basées sur les arguments avec lesquels votre script est lancé. [`$argc`][argc] est une variable d'entier contenant le *nombre* d'arguments et [`$argv`][argv] est un tableau de variables contenant chacune la *valeur* d'un argument. Le premier argument est toujours le nom de votre fichier de script PHP, dans notre cas `hello.php`.

L'expression `exit()` est utilisée avec un nombre différent de zéro pour indiquer au shell que la commande a échoué. Les usages communs du code exit peuvent être trouvés [ici][exit-codes].

Pour lancer notre script, à partir de la ligne de commande :

{% highlight bash %}
> php hello.php
Usage: php hello.php [name]
> php hello.php world
Hello, world
{% endhighlight %}


 * [Apprendre comment lancer PHP en ligne de commande][php-cli]
 * [Apprendre comment configurer Windows pour lancer PHP en ligne de commande][php-cli-windows]

[phpinfo]: http://php.net/manual/fr/function.phpinfo.php
[cli-options]: http://www.php.net/manual/fr/features.commandline.options.php
[argc]: http://php.net/manual/fr/reserved.variables.argc.php
[argv]: http://php.net/manual/fr/reserved.variables.argv.php
[php-cli]: http://php.net/manual/fr/features.commandline.php
[php-cli-windows]: http://www.php.net/manual/fr/install.windows.commandline.php
[exit-codes]: http://www.gsp.com/cgi-bin/man.cgi?section=3&topic=sysexits
