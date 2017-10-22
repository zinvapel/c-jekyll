---
layout: page
title: Генерация ссылок
category: customization
---

Jekyll предоставляет возможность конфигурировать внешний вид ссылок. Это можно сделать во [Front Matter][yml] или же в `_config.yml`.
По-умолчанию используется `/:categories/:year/:month/:day/:title.html`. При этом доступны следующие плейсхолдеры:
- `year` - год
- `month` - месяц
- `i_month` - месяц без ведущего нуля
- `day` - день
- `i_day` - день без ведущего нуля
- `y_day` - день в году с ведущим нулем
- `short_year` - год без века
- `hour` - час берется из описания [Front Matter][yml]
- `minute` - минута берется из описания [Front Matter][yml]
- `second` - секунда  берется из описания [Front Matter][yml]
- `title` - имя файла с постом без времени
- `slug` - берется имя файла без даты (удаляются все нечисловые и небуквенные символы). Может быть перезаписан из `slug` переменной [Front Matter][yml]
- `categories` - категории из поста в формате `/category1/category2/...`

Существуют также встроенные стили ссылок, которые доступны только в `_config.yml`:
- `date` - по-умолчанию `/:categories/:year/:month/:day/:title.html`
- `pretty` - `/:categories/:year/:month/:day/:title/`
- `ordinal` - `/:categories/:year/:y_day/:title.html`
- `none` - `/:categories/:title.html`

Разумеется можно использовать любые дополнительные строковые значения в ссылках, например `/blog/:year/:month/:day/:title/`.
Как задавать ссылки для [страниц]({{ site.baseurl }}{% post_url 2017-10-18-page-creating %}) и [коллекций]({{ site.baseurl }}{% post_url 2017-10-20-collections %}) указанно на их страницах.

[yml]: {{ site.baseurl }}{% post_url 2017-10-16-front-matter %}
