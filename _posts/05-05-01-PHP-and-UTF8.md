---
назва: Робота з UTF-8
isChild: true
якір: php_and_utf8
title: "Робота з UTF-8"
---

## Робота з UTF-8 {#php_and_utf8_title}

_Цей розділ спочатку був написаний [Alex Cabal](https://alexcabal.com/) о
[Найкращі практики PHP](https://phpbestpractices.org/#utf-8) і було використано як основа для наших власних порад щодо UTF-8_.

### Немає однострокового. Будьте уважними, детальними та послідовними.

Зараз PHP не підтримує Unicode на низькому рівні. Є способи переконатися, що рядки UTF-8 обробляються нормально,
але це нелегко, і вимагає вивчення майже всіх рівнів веб-програм, від HTML до SQL і PHP. Ми будемо цілитися
для короткого практичного резюме.

### UTF-8 на рівні PHP

Базові операції над рядками, такі як об’єднання двох рядків і призначення рядків змінним, нічого не потребують
спеціально для UTF-8. Однак деякі рядки функцій, такі як `strpos()` і `strlen()`, потребують особливої ​​​​уваги. ці
функції часто мають відповідник `mb_*`: наприклад, `mb_strpos()` і `mb_strlen()`. Ці рядки `mb_*` зроблені
доступні через [Multibyte String Extension] і спеціально розроблені для роботи з рядками Unicode.

Ви повинні використовувати функції `mb_*` щоразу, якщо працюєте з рядком Unicode. Наприклад, якщо ви використовуєте `substr()` на a
Рядок UTF-8, є хороша ймовірність, що результат наповнює деякі спотворені напівсимволі. Правильна функція для використання
буде багатобайтовим аналогом `mb_substr()`.

Важко пам’ятати, що функції `mb_*` потрібно використовувати завжди. Якщо ви забудете хоча б один раз, ваш Unicode
рядок може бути спотворений під час подальшої обробки.

Не всі рядкові функції мають відповідник `mb_*`. Якщо немає такого для того, що ви хочете зробити, то ви можете бути поза
удачі.

Ви повинні використовувати функцію `mb_internal_encoding()` у верхній частині кожного сценарію PHP, який ви пишете (або у верхній частині вашої
global include script) і функція `mb_http_output()` відразу після нього, якщо ваш сценарій виведе в браузер.
Явне визначення кодування ваших рядків у кожному сценарії позбавить вас від багатьох головних болів у майбутньому.

Крім того, багато функцій PHP, які працюють із рядками, мають додатковий параметр, який дозволяє вказати символ
кодування. Ви завжди повинні явно вказувати UTF-8, коли надається така опція. Наприклад, `htmlentities()` має
параметр для кодування символів, і ви завжди повинні вказувати UTF-8, якщо маєте справу з такими рядками. Зверніть увагу, що починаючи з PHP 5.4.0, UTF-8 є кодуванням для замовчувань для `htmlentities()` і `htmlspecialchars()`.

Нарешті, якщо ви створите розподілену програму і не можете бути впевнені, що розширення `mbstring` буде
увімкнено, тоді розгляньте можливість використання пакета [symfony/polyfill-mbstring] Composer. Цеме використовувати `mbstring`, якщо він доступний, і
залежить від функцій, відмінних від UTF-8, якщо ні.
[Multibyte String Extension]: https://www.php.net/book.mbstring
[symfony/polyfill-mbstring]: https://packagist.org/packages/symfony/polyfill-mbstring

### UTF-8 на рівні бази даних

Якщо ваш сценарій PHP отримує доступ до MySQL, існує ймовірність того, що ваші рядки можуть зберігатися в базі даних як рядки, відмінні від UTF-8
навіть якщо ви дотримуєтесь усіх наведених вище заходів безпеки.

Щоб переконатися, що ваші рядки переходять із PHP на MySQL як UTF-8, переконайтеся, що ваша база даних і таблиці налаштовані на
набір символів `utf8mb4` і сортування, а також використання набору символів `utf8mb4` у рядку з’єднання PDO. див
приклад коду нижче. Це _критично важливо_.

Зауважте, що ви повинні використовувати набір символів `utf8mb4` для повної підтримки UTF-8, а не набір символів `utf8`! див
Подальше читання, чому.

### UTF-8 на рівні браузера

Використовуйте функцію `mb_http_output()`, щоб переконатися, що ваш сценарій PHP виводить рядки UTF-8 у ваш браузер.

Відповідь HTTP має повідомити веб-переглядачу, що цю сторінку слід вважати UTF-8. Сьогодні прийнято встановлювати набір символів у заголовку відповіді HTTP таким чином:

{% highlight php %}
<?php
header('Content-Type: text/html; charset=UTF-8')
{% endhighlight %}

Історичним підходом до цього було додавання [тегу набору символів `<meta>`](http://htmlpurifier.org/docs/enduser-utf8.html) до тегу `<head>` вашої сторінки.

{% highlight php %}
<?php
// Повідомте PHP, що ми використовуємо рядки UTF-8 до кінця сценарію
mb_internal_encoding('UTF-8');
$utf_set = ini_set('default_charset', 'utf-8');
if (!$utf_set) {
    throw new Exception('не вдалося встановити default_charset на utf-8, переконайтеся, що його встановлено у вашій системі!');
}

// Повідомте PHP, що ми будемо виводити UTF-8 у браузер
mb_http_output('UTF-8');

// Наш тестовий рядок UTF-8
$string = 'El síla erin lû e-govaned vîn.';

// Певним чином трансформувати рядок за допомогою багатобайтової функції
// Зверніть увагу на те, як ми скоротили рядок на символі, відмінному від Ascii, для демонстраційних цілей
$string = mb_substr($string, 0, 15);

// Підключення до бази даних для збереження перетвореного рядка
// Для отримання додаткової інформації дивіться приклад PDO в цьому документі
// Зверніть увагу на `charset=utf8mb4` в назві джерела даних (DSN)
$link = новий PDO(
    'mysql:host=ваше ім'я хоста;dbname=ваша база даних;charset=utf8mb4',
    'ваше ім'я користувача',
    'ваш-пароль',
    масив(
        PDO::ATTR_ERRMODE => PDO::ERRMODE_EXCEPTION,
        PDO::ATTR_PERSISTENT => false
    )
);

// Зберігаємо наш перетворений рядок як UTF-8 у нашій базі даних
// Ваша БД і таблиці мають набір символів і сортування utf8mb4, вірно?
$handle = $link->prepare('вставити в ElvishSentences (Id, Body, Priority) значення (за замовчуванням, :body, :priority)');
$handle->bindParam(':body', $string, PDO::PARAM_STR);
$пріоритет = 45;
$handle->bindParam(':priority', $priority, PDO::PARAM_INT); // явно вказуємо pdo очікувати int
$handle->execute();

// Отримати рядок, який ми щойно зберегли, щоб підтвердити, що він був збережений правильно
$handle = $link->prepare('вибрати * з ElvishSentences, де Id = :id');
$id = 7;
$handle->bindParam(':id', $id, PDO::PARAM_INT);
$handle->execute();

// Зберігаємо результат в об’єкт, який ми виведемо пізніше в нашому HTML
// Цей об’єкт не вб’є вашу пам’ять, оскільки він своєчасно отримує дані
$результат = $handle->fetchAll(\PDO::FETCH_OBJ);

// Приклад оболонки, яка дозволяє вам передавати дані в html
функція escape_to_html($dirty){
    echo htmlspecialchars($dirty, ENT_QUOTES, 'UTF-8');
}

header('Content-Type: text/html; charset=UTF-8'); // Немає потреби, якщо для вашого default_charset уже встановлено значення utf-8
?><!doctype html>
<html>
    <голова>
        <meta charset="UTF-8">
        <title>Тестова сторінка UTF-8</title>
    </head>
    <тіло>
        <?php
        foreach($result as $row){
            escape_to_html($row->Body);  // Це має правильно вивести наш трансформований рядок UTF-8 у браузер
        }
        ?>
    </body>
</html>
{% endhighlight %}

### Подальше читання

* [PHP Manual: String Operations](https://www.php.net/language.operators.string)
* [PHP Manual: String Functions](https://www.php.net/ref.strings)
    * [`strpos()`](https://www.php.net/function.strpos)
    * [`strlen()`](https://www.php.net/function.strlen)
    * [`substr()`](https://www.php.net/function.substr)
* [Посібник PHP: Функції багатобайтових рядків](https://www.php.net/ref.mbstring)
    * [`mb_strpos()`](https://www.php.net/function.mb-strpos)
    * [`mb_strlen()`](https://www.php.net/function.mb-strlen)
    * [`mb_substr()`](https://www.php.net/function.mb-substr)
    * [`mb_internal_encoding()`](https://www.php.net/function.mb-internal-encoding)
    * [`mb_http_output()`](https://www.php.net/function.mb-http-output)
    * [`htmlentities()`](https://www.php.net/function.htmlentities)
    * [`htmlspecialchars()`](https://www.php.net/function.htmlspecialchars)
* [Переповнення стека: які фактори роблять PHP Unicode несумісним?](https://stackoverflow.com/questions/571694/what-factors-make-php-unicode-incompatible)
* [Переповнення стека: найкращі практики PHP і MySQL із міжнародними рядками](https://stackoverflow.com/questions/140728/best-practices-in-php-and-mysql-with-international-strings)
* [Як підтримувати повний Юнікод у базах даних MySQL](https://mathiasbynens.be/notes/mysql-utf8mb4)
* [Перенесення Unicode в PHP за допомогою Portable UTF-8](https://www.sitepoint.com/bringing-unicode-to-php-with-portable-utf8/)
* [Переповнення стека: DOMDocument loadHTML неправильно кодує UTF-8](https://stackoverflow.com/questions/8218230/php-domdocument-loadhtml-not-encoding-utf-8-correctly)
