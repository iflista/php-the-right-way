---
title: Керівництво з написання коду
---
# Керівництво з написання коду

Світ PHP великий та різноманітний, він складається з незліченних бібліотек, фреймворків та компонентів. Це спільне для PHP розробників, можливість обирати кілька з них та обєднувати в одному проекті. Важливо, щоб PHP код притримувався, на стільки, на скільки можливо, загальної стилістики коду, щоб полегшити розробникам змішування та поєднання різноманітних бібліотек для їх проектів.

[Група Взаємодії Фреймворків][fig] (раніше відома, як 'Група PHP Стандартів') запропонувала та схвалила серію рекомендацій по стилю кодування, відомих як [PSR-0][psr0], [PSR-1][psr1] і [PSR-2][psr2]. Не дозволяйте цим смішним іменам спантеличити вас, ці рекомендації всього лиш набір правил, котрі деякі проекти, такі як Drupal, Zend, CakePHP, phpBB, AWS SDK, FuelPHP, Lithium, та інші починають впроваджувати. Ви можете почати використовувати їх для своїх власних проектів або продовжувати використовувати ваш власний стиль.

В ідеалі ви повинні писати код, котрий притримується одного або кількох із цих стандартів, щоб інші розробники могли легко читати і працювати з вашим кодом. Всі вони добавляють вимоги до попередньої рекомендації, отож використання PSR-1 вимагає PSR-0, але не вимагає PSR-2.

* [Read about PSR-0][psr0]
* [Read about PSR-1][psr1]
* [Read about PSR-2][psr2]
* [Read about PSR-4][psr4]
* [Read about PEAR Coding Standards][pear-cs]
* [Read about Zend Coding Standards][zend-cs]
* [Read about Symfony Coding Standards][symfony-cs]

Ви можете використовувати [PHP_CodeSniffer][phpcs], для перевірки коду на відповідність цим рекомендаціям, додатки до текстових редакторів; [Sublime Text 2][st-cs] або подібні для отримання допомоги у реальному часі. 

Використовуйте [Налагоджувач стандартів кодування PHP][phpcsfixer] Фаб'єна Потенсьєра для автоматичної зміни синтаксису вашого коду, щоб він відповідав цим стандартам, це позбавить вас від виправлення кожної проблеми вручну.

Слід використовувати англійську для іменування. Коментарі  можуть бути на будь-якій мові, зручній для усіх, хто працює з кодом або буде працювати у майбутньому.

[fig]: http://www.php-fig.org/
[psr0]: https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-0.md
[psr1]: https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-1-basic-coding-standard.md
[psr2]: https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-2-coding-style-guide.md
[psr4]: https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-4-autoloader.md
[pear-cs]: http://pear.php.net/manual/en/standards.php
[zend-cs]: http://framework.zend.com/wiki/display/ZFDEV2/Coding+Standards
[symfony-cs]: http://symfony.com/doc/current/contributing/code/standards.html
[phpcs]: http://pear.php.net/package/PHP_CodeSniffer/
[st-cs]: https://github.com/benmatselby/sublime-phpcs
[phpcsfixer]: http://cs.sensiolabs.org/
