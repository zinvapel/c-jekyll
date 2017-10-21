---
layout: post
title: Установка и настройка
category: main
tags:
  - index-category
  - getting-started
---
## Что такое Jekyll
Jekyll - это простой генератор статический сайтов. Jekyll позволяет хранить страницы в конвертируемом формате, таким как Markdown, или же использовать [Liquid]. Это позволяет использовать его для создания блогов, так Jekyll использует GitHub Pages.

## Установка
Для того чтобы использовать Jekyll, у вас должны быть установлены:
- [Ruby] версии 2.1 и старше
- [RubyGems]
- GCC и Make

<!--more-->
Для установки используем RubyGems:
```bash
gem install jekyll bundler
```
Можно установить последнюю RC версию или конкретную версию
```bash
gem install jekyll --pre
gem install jekyll -v '2.0.0.alpha.1'
```

## Создане нового сайта
Для создания сайта используется команда
```bash
jekyll new <PATH>
```
Чтобы установить в текущую директорию используется команда
```bash
jekyll new .
```
Если директория не пустая, то можно добавить опцию `--force`.  
Jekyll автоматически вызывает `bundle install`, чтобы установить зависимости, эту опцию можно опустить с помощью `--skip-bundle`.  
Также Jekyll ставить [тему][jekyll-theme] Minima, чтобы начать с нуля используется опция `--blank`.

## Базовое использование
Чтобы собрать сайт с помощью Jekyll используется команды
```bash
jekyll build
# Контент из текущей директории будет сгенерирован в директорию _site

jekyll build --destination <destination>
# Контент из текущей директории будет сгенерирован в директорию <destination>

jekyll build --source <source> --destination <destination>
# Контент из директории <source> будет сгенерирован в директорию <destination>

jekyll build --watch
# Контент из текущей директории будет сгенерирован в директорию _site, при изменении контента будет автоматически перегенерировано
```

Jekyll приходит к нам вместе с встроенным сервером для разработки.
```bash
jekyll serve
# Сервер будет размещен по адресу 127.0.0.1:4000
# Контент будет автоматически перегенерирован при изменении
# Чтобы избежать этого используется опция --no-watch
# Чтобы задать кастомный порт используется опция --port <port>
# Чтобы отвязать сервер от текущего терминала (запустить в фоне) используется опция --detach
```
## Структура директорий
Типичная структура сайта имеет вид:
```bash
.
├── _config.yml
├── _data
|   └── members.yml
├── _drafts
|   ├── begin-with-the-crazy-ideas.md
|   └── on-simplicity-in-technology.md
├── _includes
|   ├── footer.html
|   └── header.html
├── _layouts
|   ├── default.html
|   └── post.html
├── _posts
|   └── 2017-10-18-first-post.md
├── _sass
|   ├── _base.scss
|   └── _layout.scss
├── _site
├── .jekyll-metadata
└── index.html
```
В кратце про каждый пункт:
- \__config.yml - конфигурационный файл
- \_drafts - неопубликованные посты
- \_includes - части страниц, которые можно будет испортировать с помощью [Liquid]
- \_layouts - шаблоны для обертки вокруг постов, содержат liquid тэг `{{ "{{ content " }}}}`
- \_posts - сами посты в формате `YEAR-MONTH-DAY-title.MARKUP`
- \_data - все данные сайта   хранятся здесь в форматах `.yml, .yaml, .json, .csv` и доступны через `site.data.filename`
- \_sass - все часть SASS файлов, которые могут быть импортированы в `main.scss` и использованы на сайте
- \_site - директория с сгенерированным сайтом (как правило находится под .gitignore)
- .jekyll-metadata - помогает jekyll понимать что было сгенерировано (также как правило находится под .gitignore)
- index.html или index.md - все файлы, которые имеют секцию [YAML Front Matter][yfm] будут трансформированы с помощью Jekyll
- Прочие файлы будут перенесены в директорию с сайтом как есть.



[Liquid]: https://github.com/Shopify/liquid/wiki/Liquid-for-Designers
[jekyll]: https://jekyllrb.com/docs
[Ruby]: #
[RubyGems]: #
[jekyll-theme]: #
[yfm]: [ymf]: {{ site.baseurl }}/content-creation/front-matter/

[prev]: index.md
[next]: configuration.md
