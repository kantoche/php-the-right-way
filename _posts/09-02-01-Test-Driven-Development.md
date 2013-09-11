---
isChild: true
---

## Test Driven Development {#test_driven_development_title}

From [Wikipedia](http://en.wikipedia.org/wiki/Test-driven_development):

> Test-driven development (TDD) is a software development process that relies on the repetition of a very short development cycle: first the developer writes a failing automated test case that defines a desired improvement or new function, then produces code to pass that test and finally refactors the new code to acceptable standards. Kent Beck, who is credited with having developed or 'rediscovered' the technique, stated in 2003 that TDD encourages simple designs and inspires confidence

Il existe plusieurs types de test différents que vous pouvez rattacher à votre application.

### Test unitaire

Un test unitaire est une approche de la programmation pour s'assurer que les fonctions, les classes et les méthodes fonctionnent de la manière attendue, depuis leur implantation et tout au long du cycle de développement. En vérifiant les valeurs reçues et retournées par diverses fonctions et méthodes, vous pouvez ainsi garantir que la logique de fonctionnement interne reste correcte. En utilisant les injections de dépendance et en construisant des classes "mock" et des conteneurs (stubs), vous pouvez vérifier que les dépendances sont utilisées de façon appropriée pour une meilleure couverture de test.

Quand vous créez une classe ou une fonction, vous devez créer un test unitaire pour chaque comportement qu'elle doit avoir. A un niveau très basique, vous devez vous assurer qu'elle renvoie une erreur si vous lui envoyez de mauvais arguments et qu'elle fonctionne correctement si les arguments sont valides. Cela aidera à garantir que, si vous faites ultérieurement des modifications à cette classe ou à cette fonction au cours du cycle de développement, la fonctionnalité initiale continuera de fonctionner comme attendu. La seule alternative à ce test serait un var_dump() dans un test.php, ce qui n'est en aucune façon une manière de construire une application - petite ou grande.

L'autre utilité des tests unitaires est de contribuer à l'open source. Si vous écrivez un test qui montre une fonctionnalité en panne (i.e. en échec), et si l'ayant réparée, le test affiche une réussite, vos correctifs auront plus de chance d'être acceptés. Si vous démarrez un projet qui acceptent des 'pull requests', vous devriez suggérer ce type de test comme une exigence.

[PHPUnit](http://phpunit.de) est le cadre de travail de facto pour écrire des test unitaires pour les applications PHP, mais il y a plusieurs alternatives :

* [SimpleTest](http://simpletest.org)
* [Enhance PHP](http://www.enhance-php.com/)
* [PUnit](http://punit.smf.me.uk/)
* [atoum](https://github.com/atoum/atoum)

### Test d'integration

From [Wikipedia](http://en.wikipedia.org/wiki/Integration_testing):

> Integration testing (sometimes called Integration and Testing, abbreviated "I&T") is the phase in software testing in which individual software modules are combined and tested as a group. It occurs after unit testing and before validation testing. Integration testing takes as its input modules that have been unit tested, groups them in larger aggregates, applies tests defined in an integration test plan to those aggregates, and delivers as its output the integrated system ready for system testing.

Beaucoup d'outils utilisés pour les tests unitaires peuvent être également utilisés pour les tests d'intégration tant les principes à l'oeuvre sont très similaires.

### Test fonctionnel

Parfois aussi appelé test d'acceptation, le test fonctionnel consiste à utiliser des outils pour réaliser des tests qui utilisent réellement votre application, plutôt que de vérifier uniquement que des unités individuelles de code se comportent correctement et que ces unités peuvent s'adresser les unes aux autres correctement. Ces outils fonctionne typiquement en utilisant de vraies données et en simulant le comportement réel des utilisateurs de l'application.

#### Outils de test fonctionnel

* [Selenium](http://seleniumhq.com)
* [Mink](http://mink.behat.org)
* [Codeception](http://codeception.com) est un cadre de test complet qui inclut des outils de test d'acceptation.
