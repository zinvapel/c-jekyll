---
layout: page
title: Создание страниц
category: content-creation
---

## Страницы
Помимо постов также есть страницы, они не имеют даты и хранятся по ссылке, по которой они лежат. Ссылку можно изменить, если задать её в опции `permalink` [Front Matter][ymf].

```jekyll
---
permalink: new-page # => {baseurl}/new-page/
---
```

## Статические файлы
Как уже говорилось, Jekyll поддерживает статические файлы. Они доступны в переменной `site.static_files` и имеют следующие свойства:
- `file.path` - относительный путь
- `file.modified_time` - время модификации
- `file.name` - имя
- `file.basename` - имя без расширения
- `file.extname` - расширения без имени

У статических файлов нет [Front Matter][ymf], но можно добавить свойства в `_config.yml`.
```yaml
defaults:
  - scope:
      path: "assets/img"
    values:
      image: true
```

```jekyll
{% raw %}
{% assign image_files = site.static_files | where: "image", true %}
{% for myimage in image_files %}
  {{ myimage.path }}
{% endfor %}
{% endraw %}
```

[ymf]: {{ site.baseurl }}/content-creation/front-matter/
[liquid]: https://github.com/Shopify/liquid/wiki/Liquid-for-Designers
