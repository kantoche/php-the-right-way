---
isChild: true
---

## Exceptions {#exceptions_title}

Les exceptions sont une partie standard des langages de programmation les plus populaires, mais elles ont souvent été négligées par les programmeurs PHP. Des langages comme Ruby sont extrémement riches en exceptions, aussi que quelque chose se passe mal comme l'échec d'une requête HTTP ou d'une requête en base, ou bien même qu'il soit impossible de trouver une ressource image, Ruby (ou les gems utilisées) renverra une exception à l'écran vous signalant instantanément qu'une erreur s'est produite.

PHP est de son côté plutôt laxiste en la matière, et un appel à `file_get_contents()` se contentera de vous renvoyer un `FALSE` et une alerte.
De nombreux cadres de travail PHP comme CodeIgniter retourneront juste un false, enregistreront un message dans leur journal d'erreur et peut-être vous laisseront utiliser une méthode comme `$this->upload->get_error()` pour savoir ce qui s'est mal passé. La difficulté ici est que vous devez rechercher l'erreur et vérifier dans la documentation à quoi correspond la méthode d'erreur pour cette classe, plutôt que d'en recevoir un compte-rendu très évident.

Un autre problème survient lorsque les classes renvoient automatiquement une erreur à l'écran et interrompent l'exécution. Lorsque vous faites cela, vous interdisez à un autre développeur de pouvoir gérer dynamiquement cette erreur. Les exceptions ne devraient être lancées que pour mettre un développeur au courant d'une erreur; il peut alors choisir la façon de la gérer. E.g.:

{% highlight php %}
<?php
$email = new Fuel\Email;
$email->subject('My Subject');
$email->body('How the heck are you?');
$email->to('guy@example.com', 'Some Guy');

try
{
    $email->send();
}
catch(Fuel\Email\ValidationFailedException $e)
{
    // The validation failed
}
catch(Fuel\Email\SendingFailedException $e)
{
    // The driver could not send the email
}
finally
{
    // Use this to let user know email was sent
}
{% endhighlight %}

### Les exceptions SPL

La classe générique `Exception` fournit très peu d'information de contexte de débogage pour le développeur; cependant, pour y remédier, il est possible de créer un type `Exception` spécialisé en sous-classant la classe générique `Exception` :

{% highlight php %}
<?php
class ValidationException extends Exception {}
{% endhighlight %}

Cela signifie que vous pouvez ajouter de multiples blocs catch et gérer différemment différentes exceptions. Cela peut conduire alors à la création d'un <em>grand nombre</em> d'exceptions spécifiques, dont certaines auraient pu être évitées en utilisant les exceptions SPL proposées par l'[extension SPL][splext]. 

Si par exemple vous utilisez la méthode magique `__call()` et qu'une méthode invalide est demandée, alors au lieu de renvoyer une exception standard qui reste vague, ou de créer une exception spécifique pour ce seul usage, vous pouvez tout simplement `throw new BadFunctionCallException;`.

* [A propos des exceptions][exceptions]
* [A propos des exceptions SPL][splexe]
* [Insérer des exceptions dans PHP][nesting-exceptions-in-php]
* [Exceptions, les bonnes pratiques en PHP 5.3][exception-best-practices53]

[exceptions]: http://php.net/manual/fr/language.exceptions.php
[splexe]: http://php.net/manual/fr/spl.exceptions.php
[splext]: /#standard_php_library
[exception-best-practices53]: http://ralphschindler.com/2010/09/15/exception-best-practices-in-php-5-3
[nesting-exceptions-in-php]: http://www.brandonsavage.net/exceptional-php-nesting-exceptions-in-php/
