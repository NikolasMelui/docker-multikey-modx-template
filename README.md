Docker Multikey Modx Template
======
##### [Russian][russian-docs]
Docker Multikey Modx Template, powered by [NikolasMelui][nikolasmelui] and [RinatDav][rinatdav] for [Multikey Studio][multikey-studio], is a powerfull orchestration platform of docker and docker-compose files includes nginx, mysql, php, gitify and modx-multikey-template.

# Important!
You need to install [Docker][docker] and [Docker-compose][docker-compose] first.

You can think this is useless template with old technologies and MODX is bad and dead. Ok.
> Go and fu** yourself. J. Stat.

## Installation

Clone this repo on your local mashine and orchestrate all composition:
```
$ docker-compose up -d
```
Once everything is installed, use bash to enter the application container named ${projectname}_php_1:
```
$ docker exec -it ${projectname}_php_1 bash
```
Now from application container use this commands to clone multikey-modx-template into it and install MODX:
```
$ git clone https://github.com/NikolasMelui/multikey-modx-template.git
$ cp ../../Gitify/Gitify modx:install
```
Gitify will ask you for details to install (all details is in __docker-compose.yml__ file):
* Database Host [localhost]: __db__
* Database Name [dockermultikeymodxtemplate]: __modx__
* Database User [root]: __root__
* Database Password: __password__
* Database Prefix [modx_]:
* Hostname []:
* Base URL [/]:
* Manager Language [en]: __ru__
* Manager User [tmp_admin]: __admin__
* Manager User Password [generated]: __password__
* Manager Email:

You can try to install all packages... but it is not a great idea, because this function is unstable.
```
$ ../../Gitify/Gitify package:install --all
```
Now build the project from static files:
```
$ ../../Gitify/Gitify build --force
```
Use this sh script to add necessary rules for files and folders:
```
$ sh rules.sh
```
And now you have a complete template.

### Quick Start

Use npm to install frontend dependencies and run browserSync and watchers to realy 'reactive' development:
```
$ npm i
$ npm run dev
```

... and this command if needed to create a minified frontend files:
```
$ npm run prod
```
##### Know more about pure [multikey-modx-template][multikey-modx-template].

## Development

Want to contribute? Great!
This is an opensource project. All contributions are welcome. Make a fork and go on!
__

| Todos | Status |
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
License
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

**From developers 2 developers.**
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
   [russian-docs]: <https://github.com/NikolasMelui/docker-multikey-modx-template/blob/master/README-ru.md>
   [multikey-studio]: <https://github.com/MultikeyStudio>
