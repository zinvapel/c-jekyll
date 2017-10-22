---
layout: page
title: Предисловие
---
Этот блог планируется размещать на GitHub Pages. Можно было бы создать статичные странички, но гораздо интереснее поиграть с современными технологиями. Именно поэтому в самом начале было решено использовать Jekyll. Это позволит углубиться и вникнуть в возможности GitHub Pages. Так же как и на странице с [документацией Jekyll][jekyll] я разобью всё на разделы. Сам прогресс создания сайта вы, возможно, сможете увидеть по коммитам, которые я постараюсь оставлять один раз в день.

## Содержание
- [Установка и настройка][1]
- [Конфигурация][1a]
- [Создание контента][1b]  
{% for post in site.categories['content-creation'] reversed %}{% unless post.tags contains 'index-category' %}  - [{{ post.title }}]({{ post.url | relative_url }})
{% endunless %}{% endfor %}
- [Кастомизация][3]  
{% for post in site.categories['customization'] reversed %}{% unless post.tags contains 'index-category' %}  - [{{ post.title }}]({{ post.url | relative_url }})
{% endunless %}{% endfor %}
- [Деплой][4]

{% assign getting_started =  site.tags['getting-started'] | first %}
{% assign configuration =  site.tags['configuration'] | first %}
{% assign content_creation =  site.tags['content-creation'] | first %}
{% assign customization =  site.tags['customization'] | first %}

[jekyll]: https://jekyllrb.com/docs

[0]: #
[1]: {{ getting_started.url | relative_url }}
[1a]: {{ configuration.url | relative_url }}
[1b]: {{ content_creation.url | relative_url }}
[2]: #
[3]: {{ customization.url | relative_url }}
[4]: #
