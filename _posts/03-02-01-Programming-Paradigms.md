---
title: Парадигми програмування
isChild: true
---

## Парадигми програмування

PHP гнучка та динамічна мова, котра підтримує різноманітя технік програмування. Вона значно розвинулася з роками, зокрема додавши солідну об'єктно-орієнтовну модель в PHP 5.0 (2004), анонімні функції та просторові імена в PHP 5.3 (2009), а також трейти в PHP 5.4 (2012). 

### Об'єктно-орієнтоване програмування

PHP має повний набір особливостей об'єктно-орієнтованого програмування, включаючи підтримку класів, абстрактних класів, інтерфейсів, наслідування, конструкторів, клонування, винятків та ін.

* [Прочитати про об'єктно орієнтований PHP][oop]
* [Прочитати про трейти][traits]

### Функціональне програмування

PHP підтримує функції першого класу, це означає, що функція може бути призначена змінній. Обидві, створені користувачем та вбудовані функції можуть посилатися на змінну та викликатися динамічно. Функції можуть бути передані як аргументи іншим функціям (ця особливість називається функцією вищого порядку), а також функція може повертати інші функції.

Рекурсія - особливіть, котра дозволяє функції викликати саму себе, це підтримується мовою, та більша частина PHP коду фокусується на ітерації.

Нові анонімні функції (з підтримкою для замикань) присутні від PHP 5.3 (2009).

PHP 5.4 добавив нову можливість зв'язувати замикання з областю видимості об'єкта, а також вдосконалено підтримку callables, так що вони можуть бути використані нарівні з анонімними функціями практично у всіх випадках.

* Продовжити читання [Функціональне програмування в PHP](/pages/Functional-Programming.html)
* [Читати про анонімні функції][anonymous-functions]
* [Читати про клас замикання][closure-class]
* [Більше інформації в Closures RFC][closures-rfc]
* [Читати про Callables][callables]
* [Читати про функції динамічного виклику з `call_user_func_array`][call-user-func-array]

### Мета програмування

PHP підтримує різноманітні форми мета програмування через такі механізми як Reflection API та Magic Methods. Доступно багато Magic Methods, таких як `__get()`, `__set()`, `__clone()`, `__toString()`, `__invoke()`, та ін. що дозволяють розробникам змінювати поведінку класу. Розробники Ruby часто говорять, що PHP бракує `method_missing`, та він доступний як `__call()` і `__callStatic()`.

* [Читати про Magic Methods][magic-methods]
* [Читати про Reflection][reflection]

[namespaces]: http://php.net/manual/en/language.namespaces.php
[overloading]: http://uk.php.net/manual/en/language.oop5.overloading.php
[oop]: http://www.php.net/manual/en/language.oop5.php
[anonymous-functions]: http://www.php.net/manual/en/functions.anonymous.php
[closure-class]: http://php.net/manual/en/class.closure.php
[callables]: http://php.net/manual/en/language.types.callable.php
[magic-methods]: http://php.net/manual/en/language.oop5.magic.php
[reflection]: http://www.php.net/manual/en/intro.reflection.php
[traits]: http://www.php.net/traits
[call-user-func-array]: http://php.net/manual/en/function.call-user-func-array.php
[closures-rfc]: https://wiki.php.net/rfc/closures
