# Конфигурация

Jekyll позволяет гибко конфигурировать сайт. Опция для конфигурации определяются через файл `_config.yml`.

## Настройки конфигурации
### Глобальные настройки
| Опция | Опция командной строки | Назначение |
| - | - | - |
| source: DIR | `-s, --source` DIR | Директория с исходниками |
| destination: DIR | `-d, --destination` DIR | Директория, в которую будет записан сайт |
| safe: BOOL | `--safe` | Выключить кастомные плагины, игнорировать симлинки |
| exclude: [DIR, FILE, ...] |  | Файлы, которые будут исключены из генерации и добавления в сайт |
| include: [DIR, FILE, ...] |  | Файлы, которые будут добавлены на сайт, несмотря на ограничения |
| timezone: TIMEZONE |  | Установить временную зону |
| encoding: ENCODING |  | Установить кодировку |

### Настройки сборки
| Опция | Опция командной строки | Назначение |
| - | - | - |
|  | `-w, --[no]-watch` | Включение авторегенерации |
|  | `--config FILE` | Указать конфиг вместо `_config.yml` |
| show_drafts: BOOL | `--drafts` | Генерировать неопубликованные посты |
|  | `JEKYLL_ENV=production` | Использовать специфичный `environment` |
| future: BOOL | `--future` | Генерировать ли посты с датой в будущем |
| unpublished: BOOL | `--unpublished` | Генерировать ли посты, которые помечены как неопубликованные |
| lsi: BOOL | `--lsi` | Создавать ли индекс для связных постов (нужен [classifier-reborn])|
| limit_posts: NUM | `--limit_posts NUM`| Ограничить количество постов для публикации |
|  | `-V, --verbose`| Детальный вывод |
|  | `-q, --quiet`| Минимальный вывод |
| incremental: BOOL | `-I, --incremental`| Включение инкрементальной сборки. Собираются только посты, которые были изменены |
| profile: BOOL | --profile | Включить отладку [Liquid] |
| strict_front_matter: BOOL | --strict_front_matter | Билд завершится ошибкой, если синтаксис неправильный в [YAML Front Matter][yfm] |

### Настройки встроенного сервера
| Опция | Опция командной строки | Назначение |
| - | - | - |
| port: PORT | `--port PORT` | Указать порт |
| host: HOSTNAME | `--host HOSTNAME` | Указать хост |
| baseurl: URL | `--baseurl URL` | Привязать к URL |
| detach: BOOL | `-B, --detach` | Запустить в фоне |
|  | `--skip-initial-build` | Пропустить сборку |
|  | `--ssl-key` | Использовать приватный ключ |
|  | `--ssl-cert` | Использовать сертификат |

## Использование настроек
### Заголовки ответа
Можно кастомизировать заголовки ответа в файле `_config.yml` с помощью ключа `webrick`.
```yaml
webrick:
  headers:
    My-Header: My-Value
    My-Other-Header: My-Other-Value
```
По-умолчанию Jekyll задает значения для `Content-Type` и `Cache-Control`

### Использование environment
Environment доступен на странице.
```liquid
{% if jekyll.environment == "production" %}
   {% include disqus.html %}
{% endif %}
```

### Настройки [Front Matter][yfm]
При написании постов часто используются повторяющиеся данные, такие как автор или макет. Вместо того, чтобы добавлять эту информацию на каждую страницу, можно указать данные настройки в файл `_config.yml` в массив по ключу `defaults`.
```yaml
defaults:
  -
    scope:
      path: "" # Пустой путь значит все файлы
    values:
      layout: "default"
      author: "Mr. Hyde"
      category: "project"
```
Каждый элемент массива `defaults` состоит из ключей
- `scope` - задает файлы для конфигурации
```yaml
path: "PATH" # Путь к файлам, можно использовать *
type: "TYPE" # Тип контента pages, posts, drafts или коллекции
```
- `values` - задает значения настроек.  
Значение ниже в массиве имеют больший приоритет, а значения на самих страницах самый высокий.

Jekyll позволяет кастомизировать еще больше - настройки процессора Markdown, директории с шаблонами, опции [Liquid]

[classifier-reborn]: http://www.classifier-reborn.com/
[Liquid]: #
[yfm]: #
