---
layout: page
title: Шаблоны
category: customization
---

В качестве движка шаблонов Jekyll использует [Liquid](https://shopify.github.io/liquid/).
Все стандартные фильтры и теги доступны. Помимо этого, Jekyll предостовляет собственные фильтры и теги для Liquid.

## Фильтры

- `relative_url` - преобразует ссылку в полную, но без хоста.

```liquid
{% raw %}
{{ "/assets/style.css" | relative_url }}
/my-baseurl/assets/style.css
{% endraw %}
```  

- `absolute_url` - преобразует ссылку в полную с хостом.  

```liquid
{% raw %}
{{ "/assets/style.css" | absolute_url }}
https://www.site.com/my-baseurl/assets/style.css
{% endraw %}
```

- `date_to_xmlschema` - преобразует дату в ISO-8601 формат.

```liquid
{% raw %}
{{ site.time | date_to_xmlschema }}
2008-11-07T13:07:54-08:00
{% endraw %}
```

- `date_to_rfc822` - преобразует дату в RFC-822 формат.

```liquid
{% raw %}
{{ site.time | date_to_rfc822 }}
Mon, 07 Nov 2008 13:07:54 -0800
{% endraw %}
```

- `date_to_string` - преобразует дату в строковый короткий формат.

```liquid
{% raw %}
{{ site.time | date_to_string }}
07 Nov 2008
{% endraw %}
```

- `date_to_long_string` - преобразует дату в строковый длинный формат.

```liquid
{% raw %}
{{ site.time | date_to_long_string }}
07 November 2008
{% endraw %}
```

- `where` - выбирает все объекты из массива, в которых по указанному ключу - указанное значение.

```liquid
{% raw %}
{{ site.members | where:"graduation_year","2014" }}
{% endraw %}
```

- `where_exp` - выбирает все объекты из массива, в которых выполняется булевое условие.

```liquid
{% raw %}
{{ site.members | where_exp:"item",
"item.graduation_year == 2014" }} {{ site.members | where_exp:"item",
"item.graduation_year < 2014" }} {{ site.members | where_exp:"item",
"item.projects contains 'foo'" }}
{% endraw %}
```

- `group_by` - группирует массив объектов по указанному свойству.

```liquid
{% raw %}
{{ site.members | group_by:"graduation_year" }}
[{"name"=>"2013", "items"=>[...]},
{"name"=>"2014", "items"=>[...]}]
{% endraw %}
```

- `group_by_exp` - группирует массив объектов по указанному условию.

```liquid
{% raw %}
{{ site.members | group_by_exp:"item",
"item.graduation_year | truncate: 3, \"\"" }}
[{"name"=>"201...", "items"=>[...]},
{"name"=>"200...", "items"=>[...]}]
{% endraw %}
```

- `xml_escape` - экранирует текст для XML.

```liquid
{% raw %}
{{ page.content | xml_escape }}
{% endraw %}
```

- `cgi_escape` - экранирует текст для использования в URL.

```liquid
{% raw %}
{{ "foo, bar; baz?" | cgi_escape }}
foo%2C+bar%3B+baz%3F
{% endraw %}
```

- `uri_escape` - экранирует текст для использования в URL.

```liquid
{% raw %}
{{ "http://foo.com/?q=foo, \bar?" | uri_escape }}
http://foo.com/?q=foo,%20%5Cbar?
{% endraw %}
```

- `number_of_words` - считает количество слов.

```liquid
{% raw %}
{{ page.content | nuber_of_words }}
1337
{% endraw %}
```

- `array_to_sentence_string` - преобразует массив в предложение.

```liquid
{% raw %}
{{ page.tags | array_to_sentence_string }}
foo, bar, and baz
{{ page.tags | array_to_sentence_string: 'or' }}
foo, bar, or baz
{% endraw %}
```

- `markdownify` - конвертирует HTML в MD.

```liquid
{% raw %}
{{ page.excerpt | markdownify }}
{% endraw %}
```

- `smartify` - конвертирует кавычки.

```liquid
{% raw %}
{{ page.title | smartify }}
{% endraw %}
```

- `scssify` - собирает CSS.

```liquid
{% raw %}
{{ some_scss | scssify }} {{ some_sass | sassify }}
{% endraw %}
```

- `slugify` - преобразует строку.

```liquid
{% raw %}
{{ "The _config.yml file" | slugify }}
the-config-yml-file
{{ "The _config.yml file" | slugify: 'pretty' }}
the-_config.yml-file
{% endraw %}
```

- `jsonify` - конвертирует массив в JSON.

```liquid
{% raw %}
{{ site.data.projects | jsonify }}
{% endraw %}
```

- `normalize_whitespace` - все пробелы приводит к единому типу.

```liquid
{% raw %}
{{ "a \n b" | normalize_whitespace }}
{% endraw %}
```

- `sort` - сортирует массив.

```liquid
{% raw %}
{{ page.tags | sort }}
{{ site.posts | sort: 'author' }}
{{ site.pages | sort: 'title', 'last' }}
{% endraw %}
```

- `sample` - выбирает одно или несколько случайных значений из массива.

```liquid
{% raw %}
{{ site.pages | sample }}
{{ site.pages | sample:2 }}
{% endraw %}
```

- `to_integer` - приводит строку к числу.

```liquid
{% raw %}
{{ some_var | to_integer }}
{% endraw %}
```

- Функции для работы с массивом. **Не изменяет массив.**

```liquid
{% raw %}
{{ page.tags | push: 'Spokane' }}
['Seattle', 'Tacoma', 'Spokane']
{{ page.tags | pop }}
['Seattle']
{{ page.tags | shift }}
['Tacoma']
{{ page.tags | unshift: "Olympia" }}
['Olympia', 'Seattle', 'Tacoma']
{% endraw %}
```

- `inspect` - конфертирует объект в строку для дебага.

```liquid
{% raw %}
{{ some_var | inspect }}
{% endraw %}
```

## Теги

### Вставки

Иногда бывает необходимость переиспользовать некоторый код в разных местах. Как уже говорилось, такие части должны находится в директории `_includes`.
Чтобы импортировать такой элемент используется liquid-тег `include`.
```liquid
{% raw %}
{% include header.html %}
{% endraw %}
```

### Подсветка синтаксиса

Jekyll 3 использует встроенную подсветку синтаксиса с помощью [Rouge](http://rouge.jneen.net/). Сейчас поддерживается 130 языков.
Для более низкой версии Jekyll нужно дополнительно установить Rouge и установить значение `highlighter: rouge` в `_config.yml`.
Можно использовать подсветку синтаксиса языков с помощью [Pygments](http://pygments.org/languages/). Для этого необходимо задать в конфигурации `highlighter: pygments`, предварительно установив:

{% highlight bash %}
gem install pygments.rb.
echo "gem 'pygments.rb'" >> Gemfile
{% endhighlight %}

При использовании подсветки можно передать два аргумента - первый имя языка, а второй - отображение номера строки
{% highlight liquid %}
{% raw %}
{% highlight ruby linenos %}
def foo
  puts 'foo'
end
{% endhighlight %}
{% endraw %}
{% endhighlight %}

### Ссылки

Тег `link` позволяет генерировать валидную ссылку на необходимы ресурс. К сожалению, эта ссылка не будет иметь `baseurl`.

{% highlight liquid %}
{% raw %}
{{ site.baseurl }}{% link _collection/name-of-document.md %}
{{ site.baseurl }}{% link _posts/2016-07-26-name-of-post.md %}
{{ site.baseurl }}{% link news/index.html %}
{{ site.baseurl }}{% link /assets/files/doc.pdf %}
{% endraw %}
{% endhighlight %}

Несколько важных замечаний
- Если ссылка будет невалидной, то Jekyll не соберет сайт.
- Нельзя использовать liquid-фильтры на ссылках.
- Чтобы создать ссылку на пост можно воспользоваться фильтром `post_url`

{% highlight liquid %}
{% raw %}
{{ site.baseurl }}{% post_url YEAR-MO-DA-name-of-post %}
{% endraw %}
{% endhighlight %}
