---
isChild: true
---

## Vagrant {#vagrant_title}

Faire tourner votre application sur différents environnements en développement et en production peut provoquer l'apparition de bogues étranges au moment de la mise en production. Il est alors astucieux de conserver différents environnements de développement à jour avec les mêmes versions de bibliothèques que celles utilisées par l'équipe de développement.
Running your application on different environments in development and production can lead to strange bugs 
popping up when you go live. It's also tricky to keep different development environments up to date with the same 
version for all libraries used when working with a team of developers. 

Si vous développez sous Windows et déployez sous Linux (ou tout système non-Windows) ou si vous développez en équipe, vous devriez envisager d'utiliser une machine virtuelle. Cela paraît compliqué, mais en utilisant [Vagrant][vagrant] vous pouvez mettre en place une simple machine virtuelle en seulement quelques étapes. Ces base boxes peuvent alors être configurées manuellement, ou vous pouvez utiliser un logiciel de "provisionnement" tel que [Puppet][puppet] ou [Chef][chef] pour le faire à votre place. Provisioning the base box est la meilleure façon de s'assurer que de multiples boxes sont configurées de manière identique et vous soulage de la contrainte de maintenir des listes compliquées de commandes d'installation. Vous pouvez également "détruire" votre machine de base et la recréer avec très peu d'étapes manuelles, cela facilitant la création d'une nouvelle installation "toute fraîche".

Vagrant crée des répertoires partagés utilisés pour distribuer votre code entre la machine hôte et la machine virtuelle, ce qui signifie que vous pouvez créer et éditer vos fichiers sur votre machine hôte et exécuter votre code au sein de votre machine virtuelle.

[vagrant]: http://vagrantup.com/
[puppet]: http://www.puppetlabs.com/
[chef]: http://www.opscode.com/
