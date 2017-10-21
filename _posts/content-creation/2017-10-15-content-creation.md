---
layout: page
title: Создание контента
category: content-creation
tag: index-category
---

Существует несколько типов контента в Jekyll, некоторые из них описаны в этом разделе.
{% for post in site.categories['content-creation'] reversed %}{% unless post.tags contains 'index-category' %}  - [{{ post.title }}]({{ post.url | absolute_url }})
{% endunless %}{% endfor %}


[ymf]: {{ site.baseurl }}/2017/10/19/front-matter.html
[liquid]: https://github.com/Shopify/liquid/wiki/Liquid-for-Designers
