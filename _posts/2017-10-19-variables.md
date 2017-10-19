---
layout: page
title: Переменные
---
## Глобальные переменные
- `site` - информация о сайте, в том числе из `_config.yml`
- `page` - информация о текущей странице и из [Front Matter][ymf]
- `layout` - информация о макете и из [Front Matter][ymf]
- `content` - информация о кентенте, доступно только из макетов.
- `paginator` - используется только когда задается опция `paginate`

## Переменные сайта
- `site.time` - время сборки сайта
- `site.pages` - список всех страниц
- `site.posts` - список всех постов
- `site.static_files` - список всех статических файлов
- `site.html_pages` - страницы, написанные на HTML
- `site.html_files` - файлы на HTML
- `site.collections` - список всех коллекций
- `site.data` - список из yaml, csv, json в папке `_data`
- `site.documents` - список всех документов в каждой коллекции
- `site.categories.CATEGORY` - список всех постов в категории CATEGORY
- `site.tags.TAG` - список всех постов с тегом TAG
- `site.url` - URL сайта
- `site.[CONFIGURATION_DATA]` - любая опция из `_config.yml`

- `NOT ENDED` -

[ymf]: {{ site.baseurl }}/2017/10/19/front-matter.html
[liquid]: #
