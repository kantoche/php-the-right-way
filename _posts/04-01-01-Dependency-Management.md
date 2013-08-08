# Gestion des dépendances {#dependency_management_title}

Il existe au choix des tonnes de bibliothèques PHP, de cadres de travail, et de composants. Votre projet aura certainement recours à plusieurs d'entre eux - ce sont les dépendances du projet. Jusqu'à recemment, PHP ne disposait pas d'un moyen efficace pour gérer ces dépendances de projet. Même si vous vous en occupiez à la main, vous deviez encore batailler avec le chargement automatique des classes. Plus maintenant.

Il y a désormais deux systèmes majeurs de gestion de paquetages pour PHP - Composer et PEAR. Lequel vous convient le mieux ? La réponse est double

 * Utilisez **Composer** lorsque vous gérez les dépendances d'un unique projet.
 * Utilisez **PEAR** lorsque vous gérez les dépendances de PHP dans leur ensemble sur votre système.

En général, les paquetages de Composer ne seront disponibles que dans les projets que vous spécifiez explicitement, tandis qu'un paquetage PEAR serait disponible pour tous vos projets PHP. Bien que PEAR pourrait sembler être l'approche la plus simple au premier coup d'oeil, il y a des avantages à utiliser une approche projet par projet pour vos dépendances.
