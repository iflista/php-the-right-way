---
isChild: true
назва: розширення MySQL
якір: mysql_extension
title: "Розширення MySQL"
---

## Розширення MySQL {#mysql_extension_title}

Розширення [mysql] для PHP неймовірно старе, його замінили два інших розширення:

- [mysqli]
- [pdo]

Розробка [mysql] не тільки минула давно, але й
**було [офіційно видалено в PHP 7.0][mysql_removed]**.

Щоб не копіюватись у своїх налаштуваннях `php.ini`, щоб побачити, який модуль ви використовуєте, одним із варіантів є пошук `mysql_*`
у обраному вами редакторі. Якщо з’явилися такі функції, як `mysql_connect()` і `mysql_query()`, то `mysql` є
у використанні.

Крім того, якщо ви не використовуєте PHP 7.x або новішу версію, якщо не вважаєте це оновлення найвищим, це призведе до більшої
труднощі, коли все-таки відбудеться оновлення PHP. Найкращий варіант – замінити використання mysql на [mysqli] або [PDO].
ваші додатки в рамках ваших власних розробок графіків, щоб потім вас не поспішали.

**Якщо ви оновлюєте [mysql] до [mysqli], слідкуйте за оновленнями ледачих посібників, які пропонують просто знайти та замінити `mysql_*` на `mysqli_*`. Мало того, що це посилене спрощення, воно втрачає переваги, які дає mysqli, наприклад зв’язування параметрів, яке також пропонується в [PDO][pdo].**

* [Підготовлені оператори MySQLi][mysqli_prepared_statements]
* [PHP: Вибір API для MySQL][mysql_api]
[mysql]: https://www.php.net/mysqli
[mysql_removed]: https://www.php.net/manual/migration70.removed-exts-sapis.php
[mysqli]: https://www.php.net/mysqli
[pdo]: https://www.php.net/pdo
[mysql_api]: https://www.php.net/mysqlinfo.api.choosing
[mysqli_prepared_statements]: https://websitebeaver.com/prepared-statements-in-php-mysqli-to-prevent-sql-injection
