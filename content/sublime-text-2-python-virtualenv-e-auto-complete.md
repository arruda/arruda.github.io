Title: Sublime Text 2 - Python, VirtualEnv e Auto Complete
Date: 2013-01-22 09:19
Author: arruda
Category: Ambiente de Trabalho, programação, Python, Selecionados
Tags: auto complete, python, sublime, text, virtualenv
Slug: sublime-text-2-python-virtualenv-e-auto-complete
Status: published
Attachments: wp-content/uploads/2013/01/Sublime_Text_Logo.png

Depois de algum tempo usando o Eclipse + PyDev, já estava ficando cansado da lentidão do Eclipse. Como já tinha usado antes o Sublime Text, mas para java, e não tinha configurado tudo para ficar com um autocomplete decente como o do eclipse, parei de usar a mesma, mas a pouco tempo descobri uma maneira rápida e facil de preparar o ambiente e que funciona muito bem, mesmo usando um virtualEnv.

Sublime Text 2 - Download
-------------------------

Antes de mais nada devemos baixar a ultima versão da IDE:  
<http://www.sublimetext.com/2>

Package Control
---------------

Para facilitar a instalação de outros pacotes no Sublime, devemos instalar esse cara aqui:  
[Package Control](http://wbond.net/sublime_packages/package_control "Package Manager").  
Para instala-lo é simples:

-   Abra o console do sublime text(**ctrl+\`** normalmente, ou acessível em **View-\>Show Console**
-   Cole o seguinte texto e de enter:

``` {lang="bash"}
import urllib2,os; pf='Package Control.sublime-package'; ipp=sublime.installed_packages_path(); os.makedirs(ipp) if not os.path.exists(ipp) else None; urllib2.install_opener(urllib2.build_opener(urllib2.ProxyHandler())); open(os.path.join(ipp,pf),'wb').write(urllib2.urlopen('http://sublime.wbond.net/'+pf.replace(' ','%20')).read()); print 'Please restart Sublime Text to finish installation'
```

Depois reinicie o sublime.

SublimeRope - Autocomplete e outras coisas do Python
----------------------------------------------------

Para instalar esse package vamos usar o Package Control recém instalado, aperte(**Shift + ctrl + P** ou no mac: **shit + cmd + P**)  
Selecione na lista: **"Package Control: Install Package"**, e na próxima lista que aparecer, procure por SublimeRope e instale.

Criando um projeto Rope
-----------------------

Para deixar tudo ok, devemos agora criar um projeto Rope e configurar alguns detalhes.  
Para criar um novo projeto Rope, aperte(**Shift + ctrl + P** ou no mac: **shit + cmd + P**), e procure por **"Rope: New Project"**.

Ao selecionar essa opção ele irá perguntar onde se encontra seu virtualenv.  
Esse é o path do env em questão, ex:  
**"/Users/arruda/.virtualenvs/um\_projeto"**  
Depois disso, caso queira add algo mais na PYTHONPATH, você pode abrir o arquivo: **".ropeproject/config.py"**

HotKeys
-------

Uma vez instalado o SublimeRope podemos usar o AutoComplete usando **Ctrl + Space**, mas existe outra funcionalidade muito boa presente no eclipse que podemos aproveitar agora no Sublime também, o Code Navigation(Navegamos diretamente para o fonte da seleção atual).

No meu caso configurei para que a hotkey para esse comando fosse: Super + A + S (No mac o super para o sublime é o Command).

Para isso devemos ir em preferences-\>Default keybinding - User e alterar no arquivo para ter a nova configuração do Rope:

``` {lang="python"}
//Rope key bindings
{ "keys": ["super+a", "super+s"], "command": "goto_python_definition", "context":
    [
        { "key": "selector", "operator": "equal", "operand": "source.python" }
    ]
}
```

Caso queira, você pode configurar outros atalhos do Rope, a lista completa se encontra aqui: [SublimeRope Keys](http://sublimerope.readthedocs.org/en/latest/key_bindings.html "http://sublimerope.readthedocs.org/en/latest/key_bindings.html")

Python Settings
---------------

Outra coisa que devemos fazer é configurar as settings do usuario para deixa-las de mais adequadas ao python.

Você pode fazer isso você deve ir em preferences-\>Settings - User, e nele por a seguinte configuração:

``` {lang="python"}
{
    "auto_complete_delay": 500,
    "detect_indentation": false,
    "folder_exclude_patterns":
    [
        ".svn",
        ".git",
        ".hg",
        "CVS",
        ".bundle",
        ".ropeproject",
        ".sass-cache",
        ".settings"
    ],
    "font_size": 13.0,
    "tab_size": 4,
    "translate_tabs_to_spaces": true,
    "trim_automatic_white_space": true,
    "trim_trailing_white_space_on_save": true
}
```

Com isso seu Sublime será uma ótima IDE para Python =)

### Referencia

Fiz esse post usando como referencia esse outro em ingles(que é muito bom e abrange outros detalhes inclusive): [Python development with Sublime Text 2 tips and tricks](http://outofmemoryblog.blogspot.com.br/2012/08/python-development-with-sublime-text-2.html "http://outofmemoryblog.blogspot.com.br/2012/08/python-development-with-sublime-text-2.html")

Abraços
