---
layout: page
title: Создание контента
category: content-creation
tag: index-category
---

Существует несколько типов контента в Jekyll, некоторые из них описаны в этом разделе.
{% for post in site.categories['content-creation'] reversed %}{% unless post.tags contains 'index-category' %}  - [{{ post.title }}]({{ site.baseurl }}{{ post.url }})
{% endunless %}{% endfor %}

[liquid]: https://github.com/Shopify/liquid/wiki/Liquid-for-Designers
