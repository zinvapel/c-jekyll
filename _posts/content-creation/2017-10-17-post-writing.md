---
title: Создание постов
category: content-creation
---
Все посты хранятся в папке `_posts`, они обязательно должны иметь [Front Matter][ymf]. Они могут быть написаны на различных языках разметки, но «из коробки» оступны Markdown и HTML.

Как уже отмечалось ранее, чтобы создать новый пост, необходимо создать файл в папке `_posts` в формате `YYYY-MM-DD-post-name.MARKUPTYPE`.
Сразу после [Front Matter][ymf] идет содержимое поста на заданном языке.
<!--more-->
Зачастую необходимо вставить в пост различные изображения, видео, ссылки на скачивание и так далее. Рекомендуется создать в корне сайта специальную директорию, например `assets`, в которую складывать все ресурсы. Так как путь до сайта может быть сконфигурирован в конфигах с помощью опции `baseurl`, то рекомендуется использовать фильтр `absolute_url`
```liquid
{% raw %}
![My avatar]({{ "/assets/ava.jpg" | absolute_url }})
{% endraw %}
```

Список всех постов хранится в массиве `site.posts`.
```liquid
{% raw %}
<ul>
  {% for post in site.posts %}
    <li>
      <a href="{{ post.url }}">{{ post.title }}</a>
    </li>
  {% endfor %}
</ul>
{% endraw %}
```

Список всех постов по категориям хранится в ассоциативном массиве `site.categories[CATEGORY]`.
Можно взять только часть поста, которая хранится в свойстве `post.excerpt`. Обрезок будет состоять из текста включительно до `excerpt_separator`, который можно задать в [Front Matter][ymf] или `_config.yml`.

```liquid
{% raw %}
---
excerpt_separator: <!--ex-->
---
Some post
<!--ex-->
Out of excerpt
{% endraw %}
```

Jekyll имеет встроенную поддержку подсветки синтаксиса. Для этого используется [Liquid][liquid]-тег `highlight`.
{% highlight liquid %}
  {% raw %}
{% highlight php %}
<?php

class Number
{
    /**
     * @var int
     */
    public $number;
}
{% endhighlight %}
  {% endraw %}
{% endhighlight %}
Вывод:
{% highlight php %}
<?php

class Number
{
    /**
     * @var int
     */
    public $number;
}
{% endhighlight %}

Отложенные посты хранятся в `_drafts`, по сути - это посты без даты. Чтобы посмотреть как сайт будет выглядеть с этими постами можно использовать опцию `--drafts` при сборке.

[ymf]: {{ site.baseurl }}/content-creation/front-matter/
[liquid]: https://github.com/Shopify/liquid/wiki/Liquid-for-Designers
