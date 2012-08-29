---
title: "Дата і час"
isChild: true
---

## Дата і час

В PHP є вбудований клас з назвою DateTime для допомоги вам коли потрібно прочитати, записати, порівняти чи порахувати дату або час. В PHP є багато функцій, повязаних з датою та часом, окрім DateTime, та клас пропонує хороший об'єктно-орієнтований інтерфейс для вирішення більшості задач. Він може обробляти часові зони, та це за межами цього короткого вступу.

Щоб почати працювати з DateTime конвертуйте необроблену строку дати та часу в об'єкт з допомогою фабричного методу `createFromFormat()` або виконайте `new \DateTime`, щоб отримати теперішню дату та час. Використовуйте метод `format()` для конвертації DateTime назад в строку для виводу.

{% highlight php %}
<?php
$raw = '22. 11. 1968';
$start = \DateTime::createFromFormat('d. m. Y', $raw);

echo "Start date: " . $start->format('m/d/Y') . "\n";
{% endhighlight %}

Обчислення з DateTime можливе з використанням класу DateInterval. DateTime містить методи `add()` та `sub()`, котрі приймають DateInterval як аргумент. Не пишіть код, котрий очікує однакове число секунд кожного дня, перевід годинника та зміна часових поясів знищать це припущення. Використовуйте замість цього інтервали дат. Для розрахунку різниці між датами використовуйте метод `diff()`. Він поверне новий DateInterval, котрий дуже легко відобразити.

{% highlight php %}
<?php
// створіть копію $start та добавте 1 місяць і 6 днів
$end = clone $start;
$end->add(new \DateInterval('P1M6D'));

$diff = $end->diff($start);
echo "Difference: " . $diff->format('%m month, %d days (total: %a days)') . "\n";
// Різниця: 1 місяць, 6 днів (всього: 37 днів)
{% endhighlight %}

З обєктами DateTime ви можете використовувати стандартні порівняння:
{% highlight php %}
<?php
if($start < $end) {
    echo "Start is before end!\n";
}
{% endhighlight %}
    
Останій приклад для демонстрації класу DatePeriod, що використовується для ітерації повторюваних подій. Він може приймати два об'єкти DateTime, початок і кінець, та інтервал для котрого він поверне всі події між об'єктами.

{% highlight php %}
<?php
// вивід всіх четвергів між $start та $end
$periodInterval = \DateInterval::createFromDateString('first thursday');
$periodIterator = new \DatePeriod($start, $periodInterval, $end, \DatePeriod::EXCLUDE_START_DATE);
foreach($periodIterator as $date)
{
    // вивід кожної дати в періоді
    echo $date->format('m/d/Y') . " ";
}
{% endhighlight %}

* [Читати про DateTime][datetime]
* [Читати про форматування дати][dateformat] (прийнятий варіант формату строки дати)

[datetime]: http://www.php.net/manual/book.datetime.php
[dateformat]: http://www.php.net/manual/function.date.php
