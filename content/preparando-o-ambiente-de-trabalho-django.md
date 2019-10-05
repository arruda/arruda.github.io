Title: Preparando o Ambiente de Trabalho - Django
Date: 2011-09-23 10:07
Author: arruda
Category: Ambiente de Trabalho, Django, programação, Python, Selecionados, Web
Tags: ambiente, Django, preparando, programação, python, trabalho, virtualenv, virtualenvwrapper, wrapper
Slug: preparando-o-ambiente-de-trabalho-django
Status: published

Agora que estou trabalhando numa nova empresa ([SparkIt](http://www.sparkit.com.br)) e havia a necessidade de documentar como preparava o ambiente de trabalho é que eu decidi fazer essa série de posts, começando com Django.

Preparando o Ambiente
---------------------

Vale ressaltar que estou considerando a instalação em um Ubuntu 11.04.

É uma ótima idéia instalar as bibliotecas a seguir, tanto para facilitar quanto para acompanhar os passos a seguir.

### PIP

Excelente ferramenta para instalar/desistalar pacotes python na sua maquina, e trabalha de forma maravilhosa com o virtualenv.

``` {lang="bash"}
$ sudo apt-get install python-setuptools python-dev build-essential
$ sudo easy_install pip
```

### Virtualenv + virtualenvwrapper

Fiz um post bem interessante, basta seguir [esses](http://www.arruda.blog.br/?p=498) passos e pronto.  
\[adsense\]

Instalando a Framework
----------------------

Antes de mais nada, crie um novo virtualenv, por exemplo:

``` {lang="bash"}
$ mkvirtualenv django1.3
```

Ative o ambiente e instale o Django:

``` {lang="bash"}
(django1.3)$ pip install Django==1.3
```

Pronto, você agora tem um ambiente com Django 1.3.

Aplicativos Interessantes
-------------------------

Para quem quer dar uma turbinada no seu Django recém instalado, aconselho estes Apps:  
[Apps Uteis Para Django](http://www.arruda.blog.br/programacao/aplicativos-uteis-para-django/)

Espero que isso de uma esclarecida, fiquem ligados pois o próximo da série será Flask!

Abraços
