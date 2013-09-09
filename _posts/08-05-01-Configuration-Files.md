---
isChild: true
---

## Fichiers de configuration {#configuration_files_title}

Lorsque vous créez des fichiers de configuration pour vos applications, les bonnes pratiques recommandent de suivre l'une de ces méthodes :

- Il est recommandé que vous stockiez vos informations de configuration à un endroit où il n'est pas possible d'y accéder directement à partir de votre système de fichiers et de les en extraire.
- Si vous devez stocker vos fichiers de configuration à la racine de votre projet, nommez-les avec une extension `.php`. Cela garantira que, s'il est possible d'accéder directement au script, son contenu ne sera pas affiché comme du texte brut.
- Les informations de vos fichiers de configuration devraient être protégées de façon appropriée, soit au moyen d'un cryptage soit par l'application des permissions du système de fichiers pour les groupes et utilisateurs.
