---
isChild: true
---

## Behavior Driven Development {#behavior_driven_development_title}

Il existe deux types différents de Behavior-Driven Development (BDD) : SpecBDD et StoryBDD. SpecBDD met l'accent sur le comportement technique ou le code, tandis que StoryBDD se focalise sur le métier, les comportements caractéristiques ou les interactions. PHP dispose de cadres de travail pour ces deux types de BDD.

Avec StoryBDD, vous écrivez des scénarios lisibles qui décrivent le comportement de votre application. Ces histoires peuvent alors servir de véritables tests pour votre application. Le cadre de travail utilisé par les applications PHP pour le StoryBDD est Behat qui est inspiré du projet [Cucumber](http://cukes.info/) de Ruby et qui intègre Gherkin DSL pour la description des traits comportementaux.

Avec SpecBDD, vous écrivez des spécifications qui décrivent comment le code devrait réellement se comporter. Plutôt que de tester une fonction ou une méthode, vous décrivez la façon dont cette fonction ou cette méthode devrait se comporter. PHP dispose du cadre de travail PHPSpec à cet effet. Ce cadre est inspiré par le [projet RSpec](http://rspec.info/) pour Ruby.

### Liens BDD    

* [Behat](http://behat.org/), cadre de travail StoryBDD pour PHP, inspiré par le projet [Cucumber](http://cukes.info/) de Ruby;
* [PHPSpec](http://www.phpspec.net/), cadre de travail SpecBDD pour PHP, inspiré par le projet [RSpec](http://rspec.info/) de Ruby;
* [Codeception](http://www.codeception.com) est un cadre de travail de test complet qui utilise les principes de BDD.
