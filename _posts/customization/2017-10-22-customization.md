---
title: Кастомизация
category: customization
tags:
  - index-category
  - customization
---

Существует несколько способов кастомизации страницы в Jekyll. Рассмотрим основные:   
{% for post in site.categories['customization'] reversed %}{% unless post.tags contains 'index-category' %}  - [{{ post.title }}]({{ post.url | relative_url }})
{% endunless %}{% endfor %}

[liquid]: https://github.com/Shopify/liquid/wiki/Liquid-for-Designers
