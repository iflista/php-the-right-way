---
isChild: правда
назва: Шари абстракції
якір: бази даних_абстракційних_шарів
---

## Шари абстракції {#databases_abstraction_layers_title}

Багато фреймворків дають власний рівень абстракції, який може розміщуватися поверх [PDO][1], а може й ні. Це часто
емулювати функції для однієї системи бази даних, яких немає в інших, загортаючи ваші запити в методі PHP, даючи
ви фактичну абстракцію бази даних, а не просто абстракцію з’єднання, яку надає PDO. Це, звичайно, додасть a
невеликі витрати, але якщо ви створите портативну програму, яка повинна працювати з MySQL, PostgreSQL і SQLite
тоді невеликі накладні витрати будуть того варті заради чистоти коду.

Деякі рівні абстракції були створені з використанням стандартів простору з іменем [PSR-0][psr0] або [PSR-4][psr4], тому їх можна
встановіть в будь-якій програмі, яка вам подобається:

* [Atlas][5]
* [Aura SQL][6]
* [Doctrine2 DBAL][2]
* [Medoo][8]
* [Propel][7]
* [laminas-db][4]

[1]: https://www.php.net/book.pdo
[2]: https://www.doctrine-project.org/projects/dbal.html
[4]: https://docs.laminas.dev/laminas-db/
[5]: https://atlasphp.io
[6]: https://github.com/auraphp/Aura.Sql
[7]: https://propelorm.org/
[8]: https://medoo.in/
[psr0]: https://www.php-fig.org/psr/psr-0/
[psr4]: https://www.php-fig.org/psr/psr-4/
