---
title: Деплой
category: deploy
---

<style>
  .right {
    float: right;
  }
  div.clear {
    clear: both;
  }
</style>
## GitHub Pages

[GitHub](https://pages.github.com/) может быть использован как хостинг. Вы можете разместить свой блог по адресу `<username>.github.io`.

Он имеет встроенную поддержку Jekyll. Есть несколько способов создать сайт.
- Создать репозиторий с именем `<username>.github.io`, он автоматически будет доступен по одноименному адресу
- Связать любой репозиторий с хостингом
  - Создать ветку с именем `gh-pages` (или же использовать `master`), в которой будет лежать исходник сайта
  - Или создать директорию с именем `docs` в ветке `master`, в которой будет лежать исходник сайта
  - Включить в настройках репозитория GitHub Pages и задать поддомен и путь до ресурсов.

Подробнее можно узнать на [сайте](https://help.github.com/articles/user-organization-and-project-pages/) проекта.

Чтобы [подготовить свой проект][readmore] к GitHub Pages нужно
- Установить gem `github-pages`

```ruby
# ./Gemfile

gem "github-pages", group: :jekyll_plugins
```

```bash
bundle update
```
- Убедиться, что используемые плагины [разрешено использовать](https://help.github.com/articles/configuring-jekyll-plugins/)
- Настроить репозиторий на публикацию

[readmore]: http://jmcglone.com/guides/github-pages/

## Continuous Integration
> Continuous Integration, или для краткости CI – это особый принцип разработки программного обеспечения, который может очень сильно упростить вам жизнь. Если на пальцах, то система CI – это некая программа, которая следит за вашим Source Control, и при появлении там изменений автоматически стягивает их, билдит, гоняет тесты (конечно, если их пишут) и возможно делает кое-что ещё. В случае же неудачи она дает об этом знать всем заинтересованным лицам, в первую очередь – последнему коммитеру.

*[habrahabr.ru](https://habrahabr.ru/post/82724/){: .right}*
<div class="clear"><br /></div>

Можно использовать любое по ПО по своему усмотрению. Авторы Jekyll указывают в документации следующие системы:
- [Travis CI](https://jekyllrb.com/docs/continuous-integration/travis-ci/)
- [CircleCI](https://jekyllrb.com/docs/continuous-integration/circleci/)
- [Buddy](https://jekyllrb.com/docs/continuous-integration/buddyworks/)

Здесь мы рассмотрим только Travis CI.
- Для начала авторизуемся в [Travis CI](https://travis-ci.org/)
- Включаем Travis для нашего репозитория `https://travis-ci.org/profile/<username>`
- Далее переходим в проект, все дальнейшие настройки будем делать в `.travis.yml` файле проекта
- Пишем скрипт для тестов
  - Самый простой тест, который мы можем выполнить - это запустить `jekyll build` и проверить, что сайт собрался
  - Чтобы проверить что именно там собралось удобно использовать [html-proofer](https://github.com/gjtorikian/html-proofer), который проверяет, что все ссылки и изображения существуют
  - Создадим скрипт проверки `./script/build`
```bash
#!/usr/bin/env bash
set -e # halt script on error

bundle exec jekyll build
bundle exec htmlproofer ./_site --disable-external
```
- Конфигурируем Travis build. Travis автоматически подтянет зависимости из Gemfile
- `.travis.yml` должен выглядеть так:

```yaml
language: ruby # Используем Ruby
rvm:
  - 2.3.3 # Используем Ruby Version Manager, версия Ruby 2.3.3

before_script: # Перед запуском тестов делаем файл исполняемым
 - chmod +x ./script/build

script: ./script/build # Сам тест

branches:
  only: # Тестируем только master-ветку
    - master

env:
  global:
  - NOKOGIRI_USE_SYSTEM_LIBRARIES=true # ускоряем установку html-proofer

sudo: false # Доступ суперпользователя нам не нужен
```

На этом всё. 
