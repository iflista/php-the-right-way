---
isChild: true
anchor:  mac_setup
---

## Налаштування macOS {#mac_setup_title}

macOS 12 (Monterey) і пізніші версії не постачаються раніше запакованими з PHP. Попередні версії macOS включають PHP, але відстають від останнього стабільного випуску. Є кілька способів встановити останню версію PHP на macOS.

### Встановіть PHP через Homebrew

[Homebrew] — це менеджер пакунків для macOS, який допоможе легко інсталювати різні PHP і розширення. Базовий репозиторій Homebrew містить «формули» для PHP 8.1, 8.2, 8.3, 8.4 і 8.5. Встановіть останню версію за допомогою цієї команди:

```
brew install php
```

Ви можете переключатися між версіями PHP Homebrew, змінюючи свою змінну `PATH`. Крім того, ви можете використовувати [brew-php-switcher][brew-php-switcher] для автоматичного перемикання версій PHP.

Ви також можете перемикати між версіями PHP вручну, об’єднавши та зв’язавши потрібну версію:

```
brew unlink php
brew link --overwrite php@8.2
```

```
brew unlink php
brew link --overwrite php@8.3
```

### Встановіть PHP через Macports

Проект [MacPorts] — це ініціатива спільноти з відкритим кодом для розробки
проста у використанні система для компіляції, встановлення та оновлення
командний рядок, програмне забезпечення з відкритим вихідним кодом на базі X11 або Aqua під керуванням macOS
система.

MacPorts підтримує попередньо скомпільовані двійкові файли, тому вам не потрібно перекомпілювати кожен
залежність від вихідних файлів tarball, це врятує ваше життя, якщо ви цього не зробите
встановити будь-який пакет у вашій системі.

На цьому етапі можна встановити `php54`, `php55`, `php56`, `php70`, `php71`, `php72`, `php73`, `php74`, `php80`, `php81`, `php82`, `php83` або `php84` за допомогою команди `port install`, наприклад:

sudo port встановити php74
порт sudo інсталювати php83

І ви можете запустити команду `select`, щоб переключити ваш активний PHP:

sudo port select --set php php83

### Встановіть PHP через phpbrew

[phpbrew] — це інструмент для встановлення кількох версій PHP і керування ними. Це може бути дуже корисно, якщо два інших
програми/проекти вимагають різні версії PHP, і ви не використовуєте віртуальні машини.

### Встановіть PHP за допомогою бінарного інсталятора Liip

Іншим популярним варіантом є [php-osx.liip.ch], який надає один метод встановлення вкладки для версій від 5.3 до 7.3.
Він не перезаписує двійкові файли PHP, встановлені Apple, але інсталює всі в окремому місці (/usr/local/php5).

### Скомпілювати з вихідного коду

Ще один варіант, який дає вам контроль над версією PHP, яку ви встановлюєте, це [компілювати його самостійно][mac-compile].
У цьому випадку переконайтеся, що встановлено [Xcode][xcode-gcc-substitution] або замінник Apple
["Інструменти командного рядка для XCode"] можна завантажити з Центру розробників Apple.

### Універсальні інсталятори

Рішення, перелічені вище, в основному обробляють сам PHP і не надають такі речі, як [Apache][apache], [Nginx][nginx] або сервер SQL.
Комплексні рішення, такі як [MAMP][mamp-downloads] і [XAMPP][xampp] встановлюють ці інші частини програмного забезпечення для
ви та зв’яжете їх усі разом, але легкість налаштування приходить із компромісом гнучкості.

[Homebrew]: https://brew.sh/
[MacPorts]: https://www.macports.org/install.php
[phpbrew]: https://github.com/phpbrew/phpbrew
[php-osx.liip.ch]: https://web.archive.org/web/20220505163210/https://php-osx.liip.ch/
[mac-compile]: https://www.php.net/install.macosx.compile
[xcode-gcc-substitution]: https://github.com/kennethreitz/osx-gcc-installer
["Command Line Tools for XCode"]: https://developer.apple.com/downloads
[apache]: https://httpd.apache.org/
[nginx]: https://www.nginx.com/
[mamp-downloads]: https://www.mamp.info/en/downloads/
[xampp]: https://www.apachefriends.org/
[brew-php-switcher]: https://github.com/philcook/brew-php-switcher
