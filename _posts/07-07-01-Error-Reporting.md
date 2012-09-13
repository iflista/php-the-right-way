---
title: Повідомлення про помилки
isChild: true
---

## Повідомлення про помилки

Логування помилок може бути корисним, при пошуку проблемних місць вашого додатку, але він також може розпізнати інформацію про структуру вашого додатку. Для ефективного захисту вашого додатку від проблем, котрі можуть бути викликані виводом цих помилок, вам потрібно налаштувати сервер по різному під час розробки і під час режиму продукту(production)(live).

### Розробка

Щоб показати помилки в вашому середовищі <strong>розробки</strong>, сконфігуруйте наступні налаштування у вашому `php.ini`:

- display_errors: On
- error_reporting: E_ALL
- log_errors: On

### Продукт

Щоб приховати помилки в вашому середовищі <strong>продукту</strong>, сконфігуруйте ваш `php.ini` як:

- display_errors: Off
- error_reporting: E_ALL
- log_errors: On

З цими налаштуваннями в виробництві, помилки все одно будуть добавлятися в лог помилок веб-сервера, та не будуть показуватися користувачу. Для отримання додаткової інформації про ці параметри, дивіться керівництво PHP:

* [Error_reporting](http://www.php.net/manual/en/errorfunc.configuration.php#ini.error-reporting)
* [Display_errors](http://www.php.net/manual/en/errorfunc.configuration.php#ini.display-errors)
* [Log_errors](http://www.php.net/manual/en/errorfunc.configuration.php#ini.log-errors)