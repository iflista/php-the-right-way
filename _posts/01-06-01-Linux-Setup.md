---
isChild: правда
якір: linux_setup
---

## Налаштування Linux {#linux_setup_title}

Більшість дистрибутивів GNU/Linux постачаються з PHP, доступними з офіційних сховищ, але ці пакети зазвичай трохи відстають від поточної стабільної версії. Є кілька способів отримати нові версії PHP для таких дистрибутивів.

### Дистрибутиви на основі Ubuntu

Наприклад, у дистрибутивах GNU/Linux на базі Ubuntu та Debian найкращі альтернативи для нативних пакетів надає та підтримує [Ондржей Сурі][Блог Ондрея Сурі] через його особистий пакет архівів (PPA) на Ubuntu та DPA/bikeshed на Debian. Знайдіть інструкції для кожного з них нижче.

Для дистрибутивів Ubuntu [PPA від Ondřej Surý][Ondrej Sury PPA] надає підтримувані версії PHP разом із багатьма розширеннями PECL. Щоб додати цей PPA до вашої системи, виконайте наступні кроки у ваших терміналах:

1. Спочатку додайте PPA до джерела програмного забезпечення вашої системи за допомогою команди:
   ```bash
   sudo add-apt-repository ppa:ondrej/php
   ```2. Після додавання PPA оновіть список пакетів вашої системи:
   ```bash
   sudo apt update
   ```Пакет гарантує, що ваша система зможе отримати доступ і встановити цей останній PHP, доступний у PPA.

### Дистрибутиви на основі Debian

Для дистрибутивів на основі Debian Ондржей Сурі також надає [bikeshed][bikeshed](еквівалент PPA у Debian). Щоб додати навіс для велосипедів у свою систему та оновити його, виконайте такі дії:

1. Переконайтеся, що у вас є root-доступ. Якщо ні, ви можете використовувати `sudo` для наступних команд.

2. Оновіть список пакетів вашої системи:
   ```bash
   sudo apt-get update
   ```3. Встановіть `lsb-release`, `ca-certificates` і `curl`:
   ```bash
   sudo apt-get -y install lsb-release ca-certificates curl
   ```4. Завантажте ключ підпису для репозиторію:
   ```bash
   sudo curl -sSLo /usr/share/keyrings/deb.sury.org-php.gpg https://packages.sury.org/php/apt.gpg
   ```5. Додайте репозиторій до джерел програмного забезпечення вашої системи:
   ```bash
   sudo sh -c 'echo "deb [signed-by=/usr/share/keyrings/deb.sury.org-php.gpg] https://packages.sury.org/php/ $(lsb_release -sc) main" > /etc/apt/sources.list.d/php.list'
   ```6. Нарешті, знову оновіть список пакетів вашої системи:
   ```bash
   sudo apt-get update
   ```Завдяки цим крокам ваша система зможе інсталювати найновіші PHP-пакети з велосипедного сараю.

### Дистрибутиви на основі RPM

У дистрибутивах на базі версії RPM (CentOS, Fedora, RHEL тощо) ви можете використовувати [репозиторій RPM Remi][remi-repo], щоб одночасно інсталювати останню PHP або мати кілька доступних версій PHP.

Існує [майстер конфігурації][remi-wizard], доступний для налаштування дистрибутива на основі RPM.

Зрештою, ви завжди можете використовувати контейнери або скомпіювати вихідний код PHP з нуля.
[Ondrej Sury Blog]: https://deb.sury.org/
[Ondrej Sury PPA]: https://launchpad.net/~ondrej/+archive/ubuntu/php
[bikeshed]: https://packages.sury.org/php/
[remi-repo]: https://rpms.remirepo.net/
[remi-wizard]: https://rpms.remirepo.net/wizard/
