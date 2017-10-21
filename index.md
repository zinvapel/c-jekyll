---
layout: page
title: Предисловие
---
Этот блог планируется размещать на GitHub Pages. Можно было бы создать статичные странички, но гораздо интереснее поиграть с современными технологиями. Именно поэтому в самом начале было решено использовать Jekyll. Это позволит углубиться и вникнуть в возможности GitHub Pages. Так же как и на странице с [документацией Jekyll][jekyll] я разобью всё на разделы. Сам прогресс создания сайта вы, возможно, сможете увидеть по коммитам, которые я постараюсь оставлять один раз в день.

## Содержание
- [Установка и настройка][1]
- [Конфигурация][1a]
- [Создание контента][1b]  
{% for post in site.categories['content-creation'] reversed %}{% unless post.tags contains 'index-category' %}  - [{{ post.title }}]({{ site.baseurl }}{{ post.url }})
{% endunless %}{% endfor %}
- [Кастомизация][3]
- [Деплой][4]

{% comment %}
========================
{% endcomment %}
{% assign getting_started =  site.tags['getting-started'] | first %}
{% assign configuration =  site.tags['configuration'] | first %}
{% assign content_creation =  site.tags['content-creation'] | first %}

[jekyll]: https://jekyllrb.com/docs

[0]: #
[1]: {{ site.baseurl }}{{ getting_started.url }}
[1a]: {{ site.baseurl }}{{ configuration.url }}
[1b]: {{ site.baseurl }}{{ content_creation.url }}
[2]: #
[3]: #
[4]: #
