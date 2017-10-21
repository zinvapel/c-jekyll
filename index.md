---
layout: page
title: Предисловие
---
Этот блог планируется размещать на GitHub Pages. Можно было бы создать статичные странички, но гораздо интереснее поиграть с современными технологиями. Именно поэтому в самом начале было решено использовать Jekyll. Это позволит углубиться и вникнуть в возможности GitHub Pages. Так же как и на странице с [документацией Jekyll][jekyll] я разобью всё на разделы. Сам прогресс создания сайта вы, возможно, сможете увидеть по коммитам, которые я постараюсь оставлять один раз в день.

## Содержание
- [Установка и настройка][1]
- [Конфигурация][1a]
- [Создание контента]({{ site.baseurl }}/content-creation/content-creation/)  
{% for post in site.categories['content-creation'] reversed %}{% unless post.tags contains 'index-category' %}  - [{{ post.title }}]({{ site.baseurl }}{{ post.url }})
{% endunless %}{% endfor %}
- [Кастомизация][3]
- [Деплой][4]

[jekyll]: https://jekyllrb.com/docs

[0]: #
[1]: {{ site.baseurl }}/main/getting-started/
[1a]: {{ site.baseurl }}/main/configuration/
[2]: #
[3]: #
[4]: #
