---
isChild: true
---

## Filtrage des données {#data_filtering_title}

Ne jamais (au grand jamais) faire confiance aux données étrangères introduites dans votre code PHP. Vous devez toujours nettoyer et valider les données étrangères avant de les utiliser dans votre code. Les fonctions `filter_var` et `filter_input` peuvent nettoyer et valider les formats de type texte (e.g. adresses email).

Les données étrangères peuvent être n'importe quoi : des données de formulaire `$_GET` et `$_POST`, des valeurs présentes dans la variable superglobale `$_SERVER`, et le corps d'une requête HTTP récupérée via `fopen('php://input', 'r')`. Rappelez-vous, les données étrangères ne sont pas limitées aux données de formulaire soumises par l'utilisateur. Les fichiers téléchargés, les valeurs de session, les données des cookies et les données en provenance de services web tiers sont aussi des données étrangères.

Bien que les données étrangères puissent être stockées, combinées et accédées ultérieurement, elles n'en demeurent pas moins des données étrangères. A chaque fois que vous traitez, affichez, concaténez, ou incluez des données dans votre code, demandez-vous si les données sont filtrées proprement et sont ainsi dignes de confiance.

Les données peuvent être _filtrées_ de manière différente en fonction du besoin. Par exemple, quand une donnée étrangère non filtrée est insérée dans une page HTML, elle peut exécuter un code HTML et JavaScript sur votre site ! Ce comportement est connu sous le nom de Cross-Site Scripting (XSS) et peut constituer une attaque très dangereuse. Une façon d'éviter XSS est de nettoyer tous les données générées par l'utilisateur avant leur affichage dans la page en supprimant les balises HTML au moyen de la fonction `strip_tags` ou en remplaçant les caractères spéciaux par les entités HTML équivalentes au moyen des fonctions `htmlentities` ou `htmlspecialchars`.

Le passage d'options devant être exécutées en ligne de commande constitue un autre exemple. Cela peut être extrémement dangereux (et c'est généralement une mauvaise idée), mais vous disposez d'une fonction intégrée `escapeshellarg` pour nettoyer les arguments de la commande exécutée.

Un dernier exemple consiste à accepter des données étrangères pour choisir un fichier à charger à partir du système de fichiers. Cette situation peut être exploitée en changeant le nom du fichier par un chemin de fichier. Vous devez supprimer "/", "../", [les octects nuls][6], ou d'autres caractères du chemin de fichier afin que les fichiers cachés, non publics ou sensibles ne puissent être chargés.

* [A propos du filtrage des données][1]
* [A propos de `filter_var`][4]
* [A propos de `filter_input`][5]
* [A propos de la gestion des octets nuls][6]

### Nettoyage

Le nettoyage supprime (ou échappe) les caractères illégaux ou douteux des données étrangères.

Par exemple, vous devriez nettoyer les données étrangères avant de les insérer dans une page HTML ou de les injecter dans une requête SQL brute. Quand vous utilisez des paramètres liés avec [PDO](#databases), il fait le travail de nettoyage pour vous.

Parfois il est nécessaire de permettre l'insertion de balises HTML autorisées lors de l'affichage d'une page HTML. C'est particulièrement délicat à réaliser et beaucoup l'évite en préférant utiliser un formatage plus restrictif comme Markdown ou BBCode, bien qu'il existe des bibliothèques de listes blanches comme [HTML Purifier][html-purifier] pour cette raison.

[Voir les filtres de nettoyage][2]

### Validation

La validation garantit que les données étrangères correspondent à ce que vous attendez. Par exemple, vous pouvez valider une adresse mail, un numéro de téléphone, ou un âge au moment du traitement d'un formulaire d'enregistrement.

[Voir les filtres de validation][3]

[1]: http://www.php.net/manual/fr/book.filter.php
[2]: http://www.php.net/manual/fr/filter.filters.sanitize.php
[3]: http://www.php.net/manual/fr/filter.filters.validate.php
[4]: http://php.net/manual/fr/function.filter-var.php
[5]: http://www.php.net/manual/fr/function.filter-input.php
[6]: http://php.net/manual/fr/security.filesystem.nullbytes.php
[html-purifier]: http://htmlpurifier.org/
