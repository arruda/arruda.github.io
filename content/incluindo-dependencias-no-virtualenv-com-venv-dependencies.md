Title: Incluindo dependências no VirtualEnv com Venv-dependencies
Date: 2011-10-24 14:39
Author: arruda
Category: Ambiente de Trabalho, Django, programação, Python
Tags: dependencia, dependencies, easy, facil, module, modulo, python, venv, virtualenv
Slug: incluindo-dependencias-no-virtualenv-com-venv-dependencies
Status: published

Após quebrar a cabeça por muito tempo no trabalho, tentando fazer o import de uma biblioteca(**pynotify**) dentro de um ambiente virtual python, eu descobri que, sei la por que razão obscura, o virtualenv não põem todas as dependências.

Uma solução comum para esse problema, é fazer uns scripts no "postmkvirtualenv" com algo do tipo:

``` {lang="bash"}
cwd=`pwd`
cdsitepackages
ln -s /usr/lib/pymodules/python2.7/gtk-2.0 .
ln -s /usr/lib/pymodules/python2.7/cairo .
ln -s /usr/lib/python2.7/dist-packages/gobject .
ln -s /usr/lib/python2.7/dist-packages/glib .
ln -s /usr/lib/python2.7/dist-packages/gtk-2.0/gio .

sed -i '1a ./gtk-2.0' easy-install.pth
sed -i '1a ./cairo' easy-install.pth
sed -i '1a ./gobject' easy-install.pth
sed -i '1a ./glib' easy-install.pth
sed -i '1a ./gio' easy-install.pth
cd $cwd
```

O Problema Dessa "Solução"
--------------------------

Na minha opinião isso é muito porco, muito ilegível, e pra você achar pra qual pasta e package você tem que fazer o link é um tanto trabalhoso(ainda mais se você está começando em python e não está familiarizado como ficam os packages).

Uma Solução Melhor
------------------

Com isso eu pensei: "Bem que podia ter uma app que você só passa um nome de um módulo python e automaticamente ele faz os links e alterações no ambiente virtual em que você se encontra pra usar o mesmo".

Com isso fiz o app **Venv-Dependencies**.  
Esse app funciona(até onde testei né) da seguinte forma:

1.  Fora de um ambiente virtual, instale o pacote, usando:

    ``` {lang="bash"}
    pip install -e git+https://github.com/arruda/venv-dependencies.git#egg=venv_dependencies
    ```

2.  Você ativa o seu ambiente virtual. Ex:

    ``` {lang="bash"}
    workon Meu-Env
    ```

3.  Agora basta executar:

    ``` {lang="bash"}
    link_venv.py "modulo"
    ```

4.  Pronto, você acabou de linkar o modulo no seu ambiente virtual
5.  Para conferir, dentro do ambiente virtual, abra o interpretador python, e faça:

    ``` {lang="python"}
    >>>import modulo
    ```

6.  Se não der erro, está tudo pronto, caso contrario, se ele disser que não conseguiu carregar o moduloX, então repita passo 3, mas dessa vez com o moduloX:

    ``` {lang="bash"}
    link_venv.py "moduloX"
    ```

Exemplos
--------

Vou citar alguns exemplos agora.  
No caso do **pynotify** esses são os modulos que precisam ser linkados:

``` {lang="bash"}
link_venv.py "gtk" "cairo" "gobject" "glib" "gio" "pango"
```

Se comparado com o trecho de código mostrado anteriormente, vê-se que realmente fica mais legível, e da mesma forma pode ser posto no **postmkvirtualenv**.

Outro exemplo que já bati muito a cabeça mas agora foi facílimo, é o módulo **pygraphviz**(usado pelo django\_extensions para fazer o grafico UML do projeto).  
Para linkar o módulo é bem simples:

``` {lang="bash"}
link_venv.py "pygraphviz"
```

  
Espero que isso ajude a muitos que tem esse problema, e para os que não querem ter.

Abraços
