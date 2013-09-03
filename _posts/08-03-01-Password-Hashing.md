---
isChild: true
---

## Hachage des mots de passe {#password_hashing_title}

Finalement toute application PHP repose sur l'enregistrement d'un utilisateur. Noms d'utilisateur et mots de passe sont stockés dans une base de données et utilisés ultérieurement pour authentifier les utilisateurs au moment de l'enregistrement.

Il est important que vous [_hachiez_][3] convenablement les mots de passe avant de les stocker. Le hachage des mots de passe est une opération à sens unique et irréversible effectuée sur le mot de passe de l'utilisateur. Cela produit une chaîne de caractère d'une longueur fixe qu'il n'est pas possible d'inverser. Cela signifie que vous pouvez comparer une valeur de hachage avec une autre afin de déterminer si les deux proviennent de la même chaîne de caractères source, mais sans pouvoir connaître la chaîne de caractère d'origine. Si les mots de passe ne sont pas hachés et qu'un tiers non autorisé accède à votre base de données, tous les comptes utilisateur sont alors compromis. Certains utilisateurs peuvent (malheureusement) utiliser le même mot de passe pour d'autres services. Il est donc important de s'occuper sérieusement de la sécurité.

**Hachage des mots de passe avec `password_hash`**

`password_hash` a été introduit dans PHP 5.5. A ce jour, il utilise BCrypt, l'algorithme actuellement le plus puissant supporté par PHP. Il sera mis à jour ultérieurement pour supporter plus d'algorithmes si nécessaire. La bibliothèque `password_compat` a été créée pour fournir une compatibilité ascendante avec PHP >= 5.3.7.

Dans l'exemple ci-dessous, nous hachons une chaîne de caractères, et nous vérifions ensuite le hachage par rapport à une nouvelle chaîne de caractères. Parce que nos deux chaînes source sont différentes ('secret-password' vs. 'bad-password') cette tentative d'enregistrement échouera.

{% highlight php %}                                                                                                                                                                                              
<?php                                                                                                                                                                                                            
require 'password.php';

$passwordHash = password_hash('secret-password', PASSWORD_DEFAULT);

if (password_verify('bad-password', $passwordHash)) {
    //Correct Password
} else {
    //Wrong password
}
{% endhighlight %}  



* [En savoir plus sur `password_hash`] [1]
* [`password_compat` pour PHP  >= 5.3.7 && < 5.5] [2]
* [En savoir plus sur le hachage en cryptographie] [3]
* [RFC PHP `password_hash`] [4]

[1]: http://us2.php.net/manual/fr/function.password-hash.php
[2]: https://github.com/ircmaxell/password_compat
[3]: http://en.wikipedia.org/wiki/Cryptographic_hash_function
[4]: https://wiki.php.net/rfc/password_hash
