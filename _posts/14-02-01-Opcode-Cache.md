---
isChild: правда
прив’язка: opcode_cache
---

## Кеш опкодів {#opcode_cache_title}

Коли PHP-файл виконується, його потрібно спочатку скомпілювати в [opcodes](https://php-legacy-docs.zend.com/manual/php4/en/internals2.opcodes) (інструкції машинної мови для ЦП). Якщо вихідний код не змінено, коди операцій залишаться тими самими, тому цей крок компіляції стає марною тратою ресурсів ЦП.

Кеш кодів операцій запобігає надлишковій компіляції, зберігаючи коди операцій у пам’яті та повторно використовуючи їх під час послідовних викликів. Як правило, спочатку перевіряється підпис або час модифікації файлу на випадок, якщо були якісь зміни.

Цілком ймовірно, що кеш коду операції значно покращить швидкість вашої програми.  Починаючи з PHP 5.5, є один вбудований - [Zend OPcache][opcache-book]. Залежно від вашого пакета/дистрибутива PHP, зазвичай його ввімкнено за умовчанням. Щоб переконатися, перевірте [opcache.enable](https://www.php.net/manual/opcache.configuration.php#ini.opcache.enable) і вихід `phpinfo()`. Для попередніх версій є розширення PECL.

Докладніше про кеші кодів операцій:

* [Zend OPcache][opcache-book](у комплекті з PHP з версії 5.5)
* Zend OPcache (раніше відомий як Zend Optimizer+) тепер називається [з відкритим кодом][Zend Optimizer+]
* [WinCache](розширення для MS Windows Server)
* [список прискорювачів PHP у Вікіпедії][PHP_accelerators]
* [Попереднє завантаження PHP] - PHP >= 7.4

[opcache-book]: https://www.php.net/book.opcache
[Zend Optimizer+]: https://github.com/zendtech/ZendOptimizerPlus
[WinCache]: https://www.iis.net/downloads/microsoft/wincache-extension
[PHP_accelerators]: https://wikipedia.org/wiki/List_of_PHP_accelerators
[PHP Preloading]: https://www.php.net/opcache.preloading
