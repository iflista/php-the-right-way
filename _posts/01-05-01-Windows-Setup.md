---
isChild: true
якір: windows_setup
title: "Налаштування Windows"
---

## Налаштування Windows {#windows_setup_title}

Ви можете завантажити двійкові файли зі [сторінки завантаження php.net][php-завантаження]. Після вилучення PHP це так
рекомендовано встановити [PATH][шлях до windows] у кореневу папку PHP (де знаходиться php.exe), щоб можна було виконувати
PHP з будь-якого місця.

Для навчання та локального розвитку ви можете використовувати [вбудований веб-сервер]({{ site.baseurl }}/#builtin_web_server_title) із PHP 5.4+, тому
вам не потрібно турбуватися про його налаштування. Якщо ви потрібен «все-в-одному», який включає повноцінний веб-сервер
і MySQL також, тоді такі інструменти, як [EasyPHP][easyphp], [OpenServer][openserver] або [WampServer][wamp] отримати результат
Середовище розробки Windows працює швидко. Проте ці інструменти будуть дещо відрізнятися від
виробництво, тому будьте обережні з відмінностями середовища, якщо ви працюєте в Windows і розгортаєтеся в Linux.

Як правило, запуск вашої програми в різних середовищах розробки та виробництва може призвести до дивних помилок
з’являється, коли ви йдете в прямому ефірі. Якщо ви розгортаєте в Windows і розгортаєте в Linux (або будь-якому іншому, що не є Windows), тоді ви
варто відшкодувати можливість використання [віртуальної машини]({{ site.baseurl }}/#virtualization_title) або [підсистеми Windows для Linux (WSL)][wsl].

Кріс Танкерслі має дуже корисну публікацію в блозі про те, які інструменти він використовує для [розробки PHP за допомогою Windows][windows-tools].
[easyphp]: https://www.easyphp.org/
[openserver]: https://ospanel.io/en/
[php-downloads]: https://www.php.net/downloads.php?os=windows
[wamp]: https://wampserver.aviatechno.net/?lang=en
[windows-path]: https://www.windows-commandline.com/set-path-command-line/
[windows-tools]: https://ctankersley.com/2016/11/13/developing-on-windows-2016/
[wsl]: https://learn.microsoft.com/en-us/windows/wsl/
