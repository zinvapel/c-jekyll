---
layout: page
title: Переменные
category: content-creation
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

## Переменные страницы
- `page.content` - содержимое страницы
- `page.title` - заголовок
- `page.excerpt` - часть страницы
- `page.url` - URL страницы /2017/10/...
- `page.date` - дата создания поста
- `page.id` - идентификатор в коллекции
- `page.categories` - массив категорий
- `page.tags` - массив тегов
- `page.path` - путь до страницы
- `page.next` - следующая страница в массиве `site.posts`
- `page.previous` - предыдущая страница в массиве `site.posts`
- `page.[FRONT_MATTER_DATA]` - любая опция из [Front Matter][ymf]

[ymf]: {{ site.baseurl }}/content-creation/front-matter/
[liquid]: https://github.com/Shopify/liquid/wiki/Liquid-for-Designers
