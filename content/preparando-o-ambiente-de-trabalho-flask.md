Title: Preparando o Ambiente de Trabalho - Flask
Date: 2011-09-26 11:23
Author: arruda
Category: Ambiente de Trabalho, programação, Python, Web
Tags: ambiente, Flask, preparando, programação, python, trabalho, virtualenv, virtualenvwrapper, wrapper
Slug: preparando-o-ambiente-de-trabalho-flask
Status: published

Dando continuidade a série "Preparando O Ambiente de Trabalho", é que vou falar sobre a Framework web chamada Flask.

Preparando o Ambiente
---------------------

Vale ressaltar que estou considerando a instalação em um Ubuntu 11.04.

Como esses passos são idênticos ao do Django, basta ver o [post](%20http://www.arruda.blog.br/?p=693) anterior essa mesma parte.

Instalando a Framework
----------------------

Antes de mais nada, crie um novo virtualenv, por exemplo:

``` {lang="bash"}
$ mkvirtualenv flask-env
```

Ative o ambiente e instale o Flask:

``` {lang="bash"}
(flask-env)$ pip install flask
```

Pronto, você agora tem um ambiente com Flask.

Apps Interessantes
------------------

Vou listar umas apps interessantes de se instalar no seu ambiente Flask:

<li>

**[Peewee](http://pypi.python.org/pypi/peewee/0.3.2)**: Uma app que permite uma interface simplista ORM com sql baseada na forma como funciona a do Django

</li>
<li>

**[Flask-FlatPages](http://packages.python.org/Flask-FlatPages/)**: Essa app providencia uma colecao de paginas para sua aplicação Flask.

</li>
<li>

**[Flask-HTMLBuilder](http://pypi.python.org/pypi/Flask-HTMLBuilder)**: Essa app permite a utilização de snippets e docs HTML completos com uma linguagem robusta para sua aplicação Flask.

</li>

Para mais apps úteis, aconselho dar uma olhada no próprio site do Flask, na seção de ["Extensions"](http://flask.pocoo.org/extensions/)

Com isso concluo esse post, estou pensando em fazer o próximo sobre alguma framework Java, ou se você tiver alguma ideia pode mandar para mim nos comentários que eu vejo se posso dar uma olhada nela.
