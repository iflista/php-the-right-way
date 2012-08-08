---
title: Інтерфейс командної строки
isChild: true
---

## Інтерфейс командної строки

PHP був створений в основному для написання веб додатків, та він також корисний для написання скриптів інтерфейсу командної строки (CLI). PHP програми для командної строки можуть допомогти вам автоматизувати спільні задачі, такі як тестування, розгортання, та адміністрування додатку.

CLI PHP програми дуже потужні, через те, що ви можете використовувати код вашого додатку напряму, без потреби в створенні і забезпеченні безпеки веб-інтерфейсу (GUI) для нього. Тільки впевніться, що ваші CLI PHP скріпти знаходяться в корені вашого веб-серверу.

Спробуйте запустити PHP з консолі:

{% highlight bash %}
> php -i
{% endhighlight %}

Опція `-i` відобразить вашу PHP конфігурацію, схоже з функцією [`phpinfo`][phpinfo].

Опція `-a` забезпечує інтерактивну оболонку, схожу з IRB ruby або інтерактивною оболонкою python. Також є цілий ряд інших корисних [опцій командної строки][cli-options].

Давайте напишемо просту "Hello, $name" CLI програму. Щоб це зробити, створіть файл з іменем `hello.php`, як показано нижче.

{% highlight php %}
<?php
if($argc != 2) {
    echo "Usage: php hello.php [name].\n";
    exit(1);
}
$name = $argv[1];
echo "Hello, $name\n";
{% endhighlight %}

PHP встановлює дві спеціальні змінні, котрі базуються на аргументах, з якими запущений ваш скріпт. [`$argc`][argc] - це змінна з числовим значенням, що містить *count* аргументів та [`$argv`][argv] - це масив, що містить значення кожного аргумента. Перший аргумент - завжди імя файлу вашого PHP скріпта, в цьому випадку це `hello.php`.

Вираз `exit()` використовується з не нульовим числом, щоб дати оболонці зрозуміти, що команда не вдалася. Часто використовувані коди завершення можна знайти [тут][exit-codes]

Щоб запустити наш скрипт із командної строки:

{% highlight bash %}
> php hello.php
Usage: php hello.php [name]
> php hello.php world
Hello, world
{% endhighlight %}


 * [Читати про запуск PHP з командної строки][php-cli]
 * [Читати про налаштування Windows для запуску PHP з командної строки][php-cli-windows]

[phpinfo]: http://php.net/manual/en/function.phpinfo.php
[cli-options]: http://www.php.net/manual/en/features.commandline.options.php
[argc]: http://php.net/manual/en/reserved.variables.argc.php
[argv]: http://php.net/manual/en/reserved.variables.argv.php
[php-cli]: http://php.net/manual/en/features.commandline.php
[php-cli-windows]: http://www.php.net/manual/en/install.windows.commandline.php
[exit-codes]: http://www.gsp.com/cgi-bin/man.cgi?section=3&topic=sysexits