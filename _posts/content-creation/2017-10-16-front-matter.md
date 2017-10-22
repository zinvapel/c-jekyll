---
title: Front Matter
category: content-creation
---
С YAML Front Matter начинается вся красота Jekyll. Front Matter должен быть в начале файла, находится между двумя тройными линиями и быть валидным YAML. Здесь можно установить значения переменным Jekyll, а также завести свои переменные.
<!--more-->
```yml
---
layout: page
title: Front Matter
---
```
Предустановленные переменные:
- `layout` - устанавливает шаблон (по-умолчанию default)
- `permalink` - ссылка на пост (по-умолчанию /year/month/day/title.html)
- `published` - флаг, говорящий о необходимости публикации поста (по-умолчанию true)

Все остальные переменные могут быть использованы в [Liquid][liquid].
Переменные для поста:
- `date` - дата поста в формате `YYYY-MM-DD HH:MM:SS +/-TTTT`
- `category/categories` - можно задавать категории, путь файла также изменится при этом на `category1/category2/.../YYYY/MM/DD/post.html`.
- `tags` - теги как метадата.  

[liquid]: https://github.com/Shopify/liquid/wiki/Liquid-for-Designers
