---
isChild: true
---

## Date et heure {#date_and_time_title}

PHP dispose d'une classe nommée DateTime pour vous aider à lire, écrire, comparer ou faire des calculs avec les dates et les heures. Il y a de nombreuses fonctions PHP liées à la date et à l'heure en plus de DateTime, mais cette classe fournit une interface orientée objet pratique pour la plupart des usages ordinaires. Elle peut gérer les fuseaux horaires, mais c'est hors du cadre de cette courte introduction.

Pour démarrer avec DateTime, convertissez une chaîne de caractères brute d'une date et heure en un objet avec la fabrique `createFromFormat()` ou saisissez `new \DateTime` pour obtenir la date et heure courante. Utilisez la méthode `format()` pour convertir un objet DateTime en une chaîne de caractères pour l'affichage.
{% highlight php %}
<?php
$raw = '22. 11. 1968';
$start = \DateTime::createFromFormat('d. m. Y', $raw);

echo 'Start date: ' . $start->format('m/d/Y') . "\n";
{% endhighlight %}

Calculer avec DateTime est possible avec la classe DateInterval. DateTime dispose de méthodes comme `add()` et `sub()` qui prennent un objet DateInterval comme argument. N'écrivez pas un code qui s'attend à retrouver le même nombre de secondes chaque jour, car à la fois le passage à l'heure d'été et les altérations du fuseau horaire mettent à mal cette supposition. Utilisez plutôt des intervalles de date. Pour calculer une différence de dates, utilisez la méthode `diff()`. Elle retournera un nouvel objet DateInterval, qui est très facile à afficher.
{% highlight php %}
<?php
// crée une copie de $start et ajoute un mois et 6 jours
$end = clone $start;
$end->add(new \DateInterval('P1M6D'));

$diff = $end->diff($start);
echo 'Difference: ' . $diff->format('%m month, %d days (total: %a days)') . "\n";
// Différence: 1 mois, 6 jours (total : 37 jours)
{% endhighlight %}

Sur les objets DateTime, vous pouvez utiliser une comparaison standard :
{% highlight php %}
<?php
if ($start < $end) {
    echo "Start is before end!\n";
}
{% endhighlight %}

Un dernier exemple concerne la classe DatePeriod. Elle est utilisée pour itérer sur des événements récurrents. Elle prend deux objets DateTime en paramètres, start et end, et l'intervalle dont on souhaite retourner l'ensemble des événements entre ces deux dates.
{% highlight php %}
<?php
// affiche tous les jeudis entre $start et $end
$periodInterval = \DateInterval::createFromDateString('first thursday');
$periodIterator = new \DatePeriod($start, $periodInterval, $end, \DatePeriod::EXCLUDE_START_DATE);
foreach ($periodIterator as $date) {
    // affiche chaque date de la période
    echo $date->format('m/d/Y') . ' ';
}
{% endhighlight %}

* [A propos de DateTime][datetime]
* [A propos du formatage des dates][dateformat] (options disponibles pour la mise au format d'une date en chaîne de caractères)

[datetime]: http://www.php.net/manual/book.datetime.php
[dateformat]: http://www.php.net/manual/function.date.php
