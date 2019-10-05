Title: Sublime Text 3 - Python,  VirtualEnv e Autocomplete
Date: 2015-01-31 18:28
Author: arruda
Category: Ambiente de Trabalho, programação, Python, Selecionados
Tags: anaconda, auto complete, flakes, lint, nicki minaj, pep, python, sublime, sublime text 3, text, virtualenv
Slug: sublime-text-3-python-virtualenv-e-autocomplete
Status: published
Attachments: wp-content/uploads/2015/01/python_anaconda.jpg

[![Python Anaconda]({static}wp-content/uploads/2015/01/python_anaconda.jpg){.aligncenter .size-full .wp-image-2411 width="283" height="272"}]({static}wp-content/uploads/2015/01/python_anaconda.jpg)

Aproveitando que muitas pessoas vem me perguntando como integrar facilmente o Python no SublimeText 3, e como meu [post anterior](http://www.arruda.blog.br/programacao/sublime-text-2-python-virtualenv-e-auto-complete/ "Sublime Text 2 – Python, VirtualEnv e Auto Complete") não funciona mais para essa nova versão da IDE, foi que decidi fazer esse post explicando como integrar essas maravilhas.

\[adsense\]

Sublime Text 3
--------------

Para fazer download é simples, basta ir em <http://www.sublimetext.com/3> e baixar a ultima versão da IDE compatível com seu sistema operacional.

Package Control
---------------

Esse carinha chamado [Package Control](https://packagecontrol.io/installation#st3 "Package control") facilita a instalação de novos pacotes no sublime text, e é muito simples de instalar:

-   Abra o console do sublime text(**ctrl+\`** normalmente, ou acessível em **View-\>Show Console**)
-   Cole o seguinte texto e de enter:

``` {lang="python"}
import urllib.request,os,hashlib; h = '2deb499853c4371624f5a07e27c334aa' + 'bf8c4e67d14fb0525ba4f89698a6d7e1'; pf = 'Package Control.sublime-package'; ipp = sublime.installed_packages_path(); urllib.request.install_opener( urllib.request.build_opener( urllib.request.ProxyHandler()) ); by = urllib.request.urlopen( 'http://packagecontrol.io/' + pf.replace(' ', '%20')).read(); dh = hashlib.sha256(by).hexdigest(); print('Error validating download (got %s instead of %s), please try manual install' % (dh, h)) if dh != h else open(os.path.join( ipp, pf), 'wb' ).write(by)
```

Em seguida reinicie o Sublime Text.

Anaconda
--------

[Anaconda](http://damnwidget.github.io/anaconda "Sublime Text Anaconda") (não, não tem nada haver com a musica da Nicki Minaj) é o package do Sublime que tem diversas coisas para facilitar sua vida na hora de desenvolver aplicações em Python no Sublime.

Com ele é possível utilizar a função de Autocompletar e navegar nos fontes de um determinado código em Python, além de usar os linters (PyFlakes ou PyLint) já "direto de fábrica".

Para instalar esse package vamos usar o Package Control recém instalado, aperte(**Shift + ctrl + P** ou no mac: **shit + cmd + P**)  
Selecione na lista: **"Package Control: Install Package"**, e na próxima lista que aparecer, procure por Anaconda e instale.

Usando o Anaconda em um Projeto
-------------------------------

Para fazer isso é muito simples, basta abrir uma pasta de algum projeto Python que esteja trabalhando, e salvar a mesma como sendo um Projeto do próprio Sublime Text.

Isso pode ser feito na opção: **Project-\>Save Project As...**.

Salve o arquivo do projeto dentro da pasta do próprio projeto.

Em seguida abra o arquivo do projeto do sublime text (**seuprojeto.sublime-project**).

Ele deverá ter uma cara parecida com a seguinte:

``` {lang="json"}
{
    "folders":
    [
        {
            "follow_symlinks": true,
            "path": "."
        }
    ]
}
```

O que você vai fazer agora é colocar uma nova propriedade que vai dizer ao SublimePythonIDE onde está o seu interpretador Python:

``` {lang="json"}
{
    "folders":
    [
        {
            "follow_symlinks": true,
            "path": "."
        }
    ],

    "settings": {
        "python_interpreter": "/home/seu_usuario/.virtualenvs/seu_projeto/bin/python"
    }
}
```

Para saber onde está o seu interpretador Python, no linux digite:

``` {lang="bash"}
$ which python
```

Com isso se você estiver usando um **VirtualEnv** (caso não esteja, aconselho ler esse post aqui e começar a usar: [Usando VirtualEnvWrapper](http://www.arruda.blog.br/programacao/python/usando-virtualenvwrapper/ "Usando VirtualEnvWrapper")), você precisa apenas ativar o seu virtualenv e rodar o mesmo comando que ele vai te mostrar onde está o interpretador Python do ambiente virtual python em questão.

HotKeys
-------

Uma vez instalado o Anaconda podemos usar o AutoComplete usando **Ctrl + Space**, mas existe outra funcionalidade muito boa presente no que podemos aproveitar agora no Sublime também, o **Go to Definition**(Navegamos diretamente para o fonte da seleção atual).

Para utilizar o **Go to Definition** no **linux** basta selecionar o bloco de codigo python que se deseja inspecionar e apertar as teclas: **Super + g**, ou no mac/windows: **ctrl+alt+g**.

Caso queira, você pode configurar outros atalhos do Anaconda ou trocar outros para que fiquem de acordo com seu gosto (eu prefiro utilizar o **Go to Definition** com **Super + a + g** por exemplo).

Linting
-------

Esse package já vem com uma série de Lints do Python built-in, como o PyFlakes e Pylint.  
Mas caso queira é possivel configurar para ele não rodar essas verificações, ou para ignorar apenas algumas, colocando nas settings a chave **anaconda\_linting** como **false**.

Existem muitas outras opções e formas de tornar o sublime text uma IDE Python bem personalizada usando o Anaconda, porém o post iria ficar imenso, se você gostou do que viu, sugiro que de uma olhada no site e veja o que mais você pode fazer para se divertir.

**OBS**: Só recomendo ser especifico na hora de buscar algo no google, ja que os primeiros resultados apontam para [Nicki Minaj](http://pt.wikipedia.org/wiki/Anaconda_(can%C3%A7%C3%A3o_de_Nicki_Minaj) "Nicki Minaji na Wiki") xD  
Abraços.
