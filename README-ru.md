Docker Multikey Modx Template
======
##### [English][english-docs]
Docker Multikey Modx Template, разработан [NikolasMelui][nikolasmelui] и [RinatDav][rinatdav] для [Multikey Studio][multikey-studio], это полноценная мощная оркестрация, представляющая собой платформу из docker и docker-compose файлов, включающая в себя nginx, mysql, php, gitify и modx-multikey-template.

# Важно!
Для корректной работы у вас на рабочей машине должны быть установлены [Docker][docker] и [Docker-compose][docker-compose].

Вы можете думать, что это бесполезный шаблон, использующий старые технологии, что MODX - мёртв и стар. Окда.
> Go and fu** yourself. J. Stat.

## Установка

Склонируйте себе этот репозиторий на рабочую машину и установите все зависимости:
```
$ git clone https://github.com/NikolasMelui/docker-multikey-modx-template.git
$ cd docker-multikey-modx-template
$ docker-compose up -d
```
Когда всё установилось, перейдите в контейнер с проектом (именуемый *_php_1) в interactive режиме с командой bash:
```
$ docker exec -it *_php_1 bash
```
На 2 уровня выше текущей директории у вас есть 2 важные папки - __Gitify__ и __Template__.
Используйте следующие команды для копирования multikey-modx-template и установки MODX Revo:
```
$ cp -r ../../Template/* ./
$ cp ../../Gitify/Gitify modx:install
```
Gitify будет спрашивать у вас информацию для установки (вся информация содержится в файле __docker-compose.yml__):
* Database Host [localhost]: __db__
* Database Name [dockermultikeymodxtemplate]: __modx__
* Database User [root]: __root__
* Database Password: __r00t__
* Database Prefix [modx_]:
* Hostname [53e5ecdbb8f1]:
* Base URL [/]:
* Manager Language [en]: __ru__
* Manager User [tmp_admin]: __admin__
* Manager User Password [generated]: __password__
* Manager Email:

Установите все пакеты (плагины MODX Revo):
```
$ ../../Gitify/Gitify package:install --all
```
Теперь "соберите" проект (сериализуйте данные из статических файлов в указанную выше базу данных):
```
$ ../../Gitify/Gitify build --force
```
И с помощью sh скрипта присвойте необходимые для корректной работы MODX Revo права и привелегии для файлов и папок:
```
$ sh rules.sh
```
На этом всё, ваш шаблон собран и проект готов.

### Быстрый старт
Используйте npm чтобы установить все frontend зависимости и запустить browserSync и "вотчеры" для настоящей "реактивной" разработки:
```
$ npm i
$ npm run dev
```

... и если вам нужно собрать минифицированные файлы - вот необходимый скрипт:
```
$ npm run prod
```
##### Узнать больше про проект [multikey-modx-template][multikey-modx-template].

## Разработка

Хотите стать разработчиком этого проекта? Супер!
Это opensource проект. Все контрибуции приветствуются. Форкайте проект себе и вперёд!

| Планы | Статус |
| ------ | ------ |
| es6 | - |
| Patterns | - |
| Webpack | - |
| ESLint | - |
| Mocha | - |
| CI\CD | - |
| SFTP\rsync | - |
| Docker | https://github.com/NikolasMelui/docker-multikey-modx-template |
| Kubernates | - |
___
Лицензия
----
MIT License

Copyright (c) 2018 NikolasMelui

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.

**От разработчиков к разработчикам.**
[NikolasMelui][nikolasmelui]
[RinatDav][rinatdav]

[//]: # (These are reference links used in the body of this note and get stripped out when the markdown processor does its job. There is no need to format nicely because it shouldn't be seen. Thanks SO - http://stackoverflow.com/questions/4823468/store-comments-in-markdown-syntax)
   [nikolasmelui]: <https://github.com/NikolasMelui>
   [rinatdav]: <https://github.com/RinatDav>
   [docker]: <https://docs.docker.com/install/>
   [docker-compose]: <https://docs.docker.com/compose/>
   [gitify]: <http://modmore.github.io/Gitify/>
   [apache]: <https://httpd.apache.org/download.cgi>
   [nginx]: <https://nginx.ru/ru/download.html>
   [php]: <http://php.net/downloads.php>
   [mysql]: <https://www.mysql.com/downloads/>
   [nodejs]: <http://nodejs.org>
   [multikey-modx-template]: <https://github.com/NikolasMelui/multikey-modx-template>
   [english-docs]: <https://github.com/NikolasMelui/docker-multikey-modx-template/blob/master/README.md>
   [multikey-studio]: <https://github.com/MultikeyStudio>
