---
title:   Virtual or Dedicated Servers
isChild: true
anchor:  virtual_or_dedicated_servers
title: "Віртуальні або виділені сервери"
---

## Віртуальні або виділені сервери {#virtual_or_dedicated_servers_title}

Якщо ви добре знаєте системне адміністрування або хочете навчитися цьому, віртуальні або виділені сервери допоможуть
Ви повністю контролюєте робоче середовище своєї програми.

### nginx і PHP-FPM

PHP, через вбудований у PHP FastCGI Process Manager (FPM), дуже добре поєднується з [nginx], який є легким,
високопродуктивний веб-сервер. Він використовує менше пам’яті, ніж Apache, і може краще обробляти більше одночасних запитів. Це є
особливо важливо на віртуальних серверах, які не мають багато вільної пам’яті.

* [Докладніше про nginx][nginx]
* [Докладніше про PHP-FPM][phpfpm]
* [Докладніше про безпечне налаштування nginx і PHP-FPM][secure-nginx-phpfpm]

### Apache і PHP

PHP і Apache мають довгу спільну історію. Apache легко налаштовується і має багато доступних
[modules][apache-modules] для розширення функціональності. Це популярний вибір для спільних серверів і легке налаштування для PHP
фреймворки та програми з відкритим кодом, такі як WordPress. На жаль, за замовчуванням Apache використовує більше ресурсів, ніж nginx
не може обслуговувати стільки відвідувачів одночасно.

Apache має кілька можливих конфігурацій для запуску PHP. Найпоширенішим і найпростішим у налаштуванні є [prefork MPM]
з `mod_php`. Хоча він не є найбільш ефективним для використання пам’яті, він найпростіший для роботи та використання. Це ймовірно
найкращий вибір, якщо ви не хочете надто глибоко копатися в аспектах адміністрування сервера. Зауважте, що якщо ви використовуєте
`mod_php` ви ПОВИННІ використовувати prefork MPM.

Крім того, якщо ви хочете вичавити більше продуктивності та стабільності з Apache, ви можете скористатися перевагами
та сама система FPM, що й nginx, і запустіть [worker MPM] або [event MPM] за допомогою mod_fastcgi або mod_fcgid. Ця конфігурація буде
бути значно ефективнішим для пам’яті та набагато швидшим, але це більше роботи для налаштування.

Якщо ви використовуєте Apache 2.4 або новішу версію, ви можете використовувати [mod_proxy_fcgi], щоб отримати чудову продуктивність, яку легко налаштувати.

* [Докладніше про Apache][apache]
* [Докладніше про багатопроцесорні модулі][apache-MPM]
* [Докладніше на mod_fastcgi][mod_fastcgi]
* [Докладніше на mod_fcgid][mod_fcgid]
* [Докладніше на mod_proxy_fcgi][mod_proxy_fcgi]
* [Докладніше про налаштування Apache і PHP-FPM за допомогою mod_proxy_fcgi][tutorial-mod_proxy_fcgi]

[nginx]: https://nginx.org/
[phpfpm]: https://www.php.net/install.fpm
[secure-nginx-phpfpm]: https://nealpoole.com/blog/2011/04/setting-up-php-fastcgi-and-nginx-dont-trust-the-tutorials-check-your-configuration/
[apache-modules]: https://httpd.apache.org/docs/2.4/mod/
[prefork MPM]: https://httpd.apache.org/docs/2.4/mod/prefork.html
[worker MPM]: https://httpd.apache.org/docs/2.4/mod/worker.html
[event MPM]: https://httpd.apache.org/docs/2.4/mod/event.html
[apache]: https://httpd.apache.org/
[apache-MPM]: https://httpd.apache.org/docs/2.4/mod/mpm_common.html
[mod_fastcgi]: https://blogs.oracle.com/opal/post/php-fpm-fastcgi-process-manager-with-apache-2
[mod_fcgid]: https://httpd.apache.org/mod_fcgid/
[mod_proxy_fcgi]: https://httpd.apache.org/docs/current/mod/mod_proxy_fcgi.html
[tutorial-mod_proxy_fcgi]: https://serversforhackers.com/video/apache-and-php-fpm
