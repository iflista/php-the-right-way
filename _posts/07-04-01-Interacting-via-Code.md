---
isChild: правда
назва: Взаємодія з базами даних
прив’язка: взаємодія з базами даних
---

## Взаємодія з базою даних {#databases_interacting_title}

Коли розробники вперше починають вивчати PHP, вони часто змішують його взаємодію з базою даних
логіка представлення, використовуючи код, який можна виглядати так:

{% highlight php %}
<ul>
<?php
foreach ($db->query('SELECT * FROM table') as $row) {
    echo "<li>".$row['field1']." - ".$row['field1']."</li>";
}
?>
</ul>
{% endhighlight %}

Це погана практика з багатьох причин, головним чином через те, що її важко налагодити, важко перевірити, важко прочитати, і це
виводитиме багато полів, якщо ви не обмежите їх.

існує хоча багато інших рішень для цього – залежно від того, чи ви віддаєте перевагу [ООП]({{ site.baseurl }}/#object-oriented-programming) чи
[функціональне програмування]({{ site.baseurl }}/#functional-programming) - має бути якийсь елемент розділення.

Розглянемо найпростіший крок:

{% highlight php %}
<?php
функція getAllFoos($db) {
    return $db->query('SELECT * FROM table');
}

$результати = getAllFoos($db);
foreach ($results as $row) {
    echo "<li>".$row['field1']." - ".$row['field1']."</li>"; // ПОГАНО!!
}
{% endhighlight %}

Це хороший початок. Помістіть ці два елементи в два різні файли, і ви отримаєте чітке розділення.

Створіть клас, щоб розповісти цей метод, і у вас буде «Модель». Створіть простий файл `.php`, щоб розмістити презентацію
логіка, і ви маєте "Вид", який дуже схожий на [MVC] - звичайну ООП-архітектуру для незалежної
[frameworks]({{ site.baseurl }}/#frameworks).

**foo.php**

{% highlight php %}
<?php
$db = new PDO('mysql:host=localhost;dbname=testdb;charset=utf8mb4', 'ім'я користувача', 'пароль');

// Зробити свою модель доступною
include 'models/FooModel.php';

// Створення екземпляра
$fooModel = новий FooModel($db);
// Отримати список Foos
$fooList = $fooModel->getAllFoos();

// Показати вигляд
включати 'views/foo-list.php';
{% endhighlight %}


**models/FooModel.php**

{% highlight php %}
<?php
клас FooModel
{
    публічна функція __construct(захищений PDO $db)
    {
    }

публічна функція getAllFoos() {
        return $this->db->query('SELECT * FROM table');
    }
}
{% endhighlight %}

**views/foo-list.php**

{% highlight php %}
<?php foreach ($fooList як $row): ?>
    <li><?= $row['field1'] ?> - <?= $row['field1'] ?></li>
<?php endforeach ?>
{% endhighlight %}

По суті, це те саме, що роблять більшість сучасних фреймворків, хоча й трохи більше вручну. Ви можете ні
потрібно робити все це щоразу, але змішування надто великої кількості логіки презентації та взаємодії з базою даних може бути а
справжня проблема, якщо ви коли-небудь захочете [модульне тестування]({{ site.baseurl }}/#unit-testing) вашої програми.

[MVC]: https://code.tutsplus.com/tutorials/mvc-for-noobs--net-10488
