---
layout: page
title: Коллекции
---

Коллекции представляют следующий тип отображений в Jekyll. Посты и страницы являются коллекциями. Jekyll предоставляет возможность создавать собственные коллекции.

Объявить коллекцию можно в `_config.yml` по опции `collections`.
```yaml
collections:
- some_collection
```
Или с дополнительными переменными
```yaml
collections:
  some_collection:
    varname: varvalue
```
Коллекции доступны атрибуты по-умолчанию. Атрибут `collections_dir` - указывает на местоположение коллекции, а сама директория с коллекцией располагается по адресу `<collections_dir>/_<collection_name>`.
```yaml
defaults:
  - scope:
      path: ""
      type: some_collection
    values:
      layout: page
```

По-умолчанию документы из коллекции не могут иметь ссылку и быть публичными, а могут только быть где-то использованы.
```liquid
{% raw %}
{% for doc in site.collections.some_collection.docs %}
  {{ doc.content }}
{% endfor %}
{% endraw %}
```

Чтобы сделать коллекцию общедоступной используется переменная `output` в `_config.yml`. Ссылку можно задать с помощью переменной `permalink`.
```yaml
collections:
  some_collection:
    output: true
    permalink: /:collection/:name
```
Для переменной `permalink` доступны плейсхолдеры:
- `:collection` - имя коллекции
- `:name` - полное имя документа
- `:path` - путь до документа, то есть будет создана директория с именем документа, а внутри будет `index.html`.
- `:title` - берется из [Front Matter][ymf] конкретного документа
- `:output_ext` - расширение файла.

Также, если будет отсутствовать [Front Matter][ymf] в документе, то от будет рассматриваться как статический файл.

Все коллекции доступны как свойство переменной сайта `site.collection_name` (появляются в виде массива документов), а все коллеции доступны в `site.collections` со свойствами:
- `label` - имя коллекции
- `docs` - массив документов коллекции
- `files` - массив файлов коллекции
- `relative_directory` - директория относительно корня сайта
- `directory` - полный путь до коллекции
- `output` - отображаемая ли коллекция

Документ коллекции имеет следующие свойства:
- `content` - контент
- `path` - полный путь до документа
- `output` - отображаемая ли коллекция
- `url` - URL без хоста
- `relative_directory` - директория относительно корня сайта
- `collection` - имя коллекции
- `date` - дата документа

Можно вынести [Front Matter][ymf] коллекции в отдельный файл с расширением разметки, а там задать дополнительные атрибуты. Пример файла attributes.md:
```yaml
---
title: "Josquin: Missa De beata virgine and Missa Ave maris stella"
artist: "The Tallis Scholars"
director: "Peter Phillips"
works:
  - title: "Missa De beata virgine"
    composer: "Josquin des Prez"
    tracks:
      - title: "Kyrie"
        duration: "4:25"
      - title: "Gloria"
        duration: "9:53"
      - title: "Credo"
        duration: "9:09"
      - title: "Sanctus & Benedictus"
        duration: "7:47"
      - title: "Agnus Dei I, II & III"
        duration: "6:49"
output: false
---
```

[ymf]: {{ site.baseurl }}/2017/10/19/front-matter.html
[liquid]: #
