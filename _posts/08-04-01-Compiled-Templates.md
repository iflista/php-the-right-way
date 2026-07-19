---
isChild: true
прив’язка: compiled_templates
title: "Зібрані шаблони"
---

## Зібрані шаблони {#compiled_templates_title}

на те, що PHP перетворився на зрілу об’єктно-орієнтовану мову, він [не значно покращився][article_templating_engines] як
мова шаблонів. Зкомпільовані шаблони, такі як [Twig], [Brainy] або [Smarty]*, заповнюють цю породу, пропонуючи новий синтаксис, який
розроблено спеціально для створення шаблонів. Від автоматичного екранування до успадкування та спрощених структур керування,
скомпільовані шаблони розроблено таким чином, щоб їх було легше писати, чистіше читати та безпечніше використовувати. Скомпільовані шаблони можуть бути навіть
поширені іншими мовами, [Mustache] є хорошим прикладом цього. Так як ці шаблони повинні бути скомпільовані
є невелике зниження продуктивності, однак воно дуже мінімальне, якщо використовується належне кешування.

**Хоча Smarty пропонує автоматичний вихід, ця функція НЕ ввімкнена за умовчанням.*

### Простий приклад скомпільованого шаблону

Використання бібліотеки [Twig].

{% highlight html+jinja %}
{% raw %}
{% include 'header.html' with {'title': 'User Profile'} %}

<h1>Профіль користувача</h1>
<p>Вітаємо, {{ name }}</p>

{% include 'footer.html' %}
{% endraw %}
{% endhighlight %}

### Приклад скомпільованих шаблонів із використанням успадкування

Використання бібліотеки [Twig].

{% highlight html+jinja %}
{% raw %}
// template.html

<html>
<голова>
    <title>{% block title %}{% endblock %}</title>
</head>
<тіло>

<головний>
    {% block content %}{% endblock %}
</main>

</body>
</html>
{% endraw %}
{% endhighlight %}

{% highlight html+jinja %}
{% raw %}
// user_profile.html

{% extends "template.html" %}

{% block title %}Профіль користувача{% endblock %}
{% block content %}
    <h1>Профіль користувача</h1>
    <p>Вітаю, {{ name }}</p>
{% endblock %}
{% endraw %}
{% endhighlight %}

[article_templating_engines]: http://fabien.potencier.org/templating-engines-in-php.html
[Twig]: https://twig.symfony.com/
[Brainy]: https://github.com/box/brainy
[Smarty]: https://www.smarty.net/
[Mustache]: https://mustache.github.io/
