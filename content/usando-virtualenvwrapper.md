Title: Usando VirtualEnvWrapper
Date: 2011-07-21 14:47
Author: arruda
Category: Python, Selecionados
Tags: pip, python, virtualenv, virtualenvwrapper, wrapper
Slug: usando-virtualenvwrapper
Status: published

Breve Revisão do VirtualEnv
---------------------------

Estive a algum tempo usando o VirtualEnv, uma ferramenta que permite diferentes ambiente virtuais de Python na mesma maquina.  
Para instalar o VirtualEnv:

``` {lang="bash"}
$ sudo pip install virtualenv
```

Com ele você pode ter um ambiente totalmente limpo com apenas os packages necessarios para um determinado projeto. Ex:  
Se estiver fazendo um projeto em Django e usando o django-extensions basta criar um virtualenv usando o comandos:

``` {lang="bash"}
$virtualenv MeuProjetoVirtual --no-site-packages --distribute
```

Em seguida basta ativar o MeuProjetoVirtual:

``` {lang="bash"}
$source /caminho/completo/MeuProjetoVirtual/bin/activate
```

Uma vez usando o virtualenv basta instalar os pacotes usando pip:  
**"pip install django" e "pip install django\_extensions"**

E pronto! Você tem agora um ambiente separado com apenas esses pacotes essenciais para seu projeto.

\[adsense\]

E o Wrapper?
------------

Pórem a magia não acaba ai, por que quando se começa a usar mais de um virtualenv, você sente uma certa dificuldade de arrumar todos eles e trocar de um para outro.

E justamente uma das grandes vantagens do VirtualEnvWrapper é a forma como ele ajuda você a organizar seus ambientes todos e trocar de um para outro com muita facilidade.  
Para instala-lo basta fazer(fora de um virtualenv):

``` {lang="bash"}
$sudo pip install virtualenvwrapper
```

Agora é preciso criar uma pasta para guardar os seus virtualenvs, por exemplo:

``` {lang="bash"}
$mkdir ~/.virtualenvs
```

Depois basta editar seu **"\~/.bashrc"** e colocar no final do mesmo:

``` {lang="bash"}
export WORKON_HOME=~/.virtualenvs
source /usr/local/bin/virtualenvwrapper.sh
```

**OBS:** dependendo da sua versão o arquivo **virtualenvwrapper.sh** pode estar num local diferente. Se este for o caso, mude o endereço para apontar para o local onde ele está.

Como Funciona?
--------------

Para criar um novo virtualenv, basta executar(de qualquer lugar) o comando:

``` {lang="bash"}
$mkvirtualenv NomeDoVirtualEnv
```

Se quiser trocar para um outro ambiente:

``` {lang="bash"}
$workon  NomeDoVirtualEnv
```

**OBS:** Se apertar TAB ele completa/mostra as opções para você.

Criando Ambientes "--no-site-packages --distribute" por Padrão
--------------------------------------------------------------

Caso queira, você pode alterar o seu **"\~/.bashrc"** e colocar no final(além do que tinha sido posto antes) o seguinte código:

``` {lang="bash"}
export VIRTUALENVWRAPPER_VIRTUALENV_ARGS='--no-site-packages --distribute'
```

Isso irá fazer com que o mkvirtualenv crie ambientes usando os argumentos **'--no-site-packages --distribute'**.

Tem mais?
---------

Pois bem, tem muito mais coisa que wrapper permite, uma das outras fantásticas coisas é a personalização dos scripts que são rodados em diversos momentos, como script que é rodado antes de criar um virtualenv, ou depois de ativar o mesmo, e etc...  
Um exemplo seria alterar o arquivo: **postmkvirtualenv**

``` {lang="bash"}
$vim $WORKON_HOME/postmkvirtualenv
```

E colocar dentro do mesmo:

``` {lang="bash"}
pip install yolk
```

Isso fará com que assim que terminar de criar o ambiente, ele irá instalar o pacote yolk no mesmo.  
Muito bom isso, principalmente para ambientes de desenvolvimento, que é bom saber quais os pacotes estão instalados.

Outro detalhe muito util que peguei com meu amigo [Victor Fontes](http://victorfontes.com/) que é limitar o pip para funcionar apenas dentro de um virtualenv, assim você não corre o risco de instalar pacotes fora de um ambiente. Para isso basta por no bashrc, antes das informações do virtualenv o seguinte:

``` {lang="bash"}
export PIP_REQUIRE_VIRTUALENV=true
```

Além disso podemos fazer com que o PIP detecte que está dentro de um virtualenv e não seja preciso passar o -E para determinar qual o ambiente atual, para isso coloque também:

``` {lang="bash"}
export PIP_RESPECT_VIRTUALENV=true
```

Para mais informações a pagina do projeto é uma ótima referência: <http://www.doughellmann.com/projects/virtualenvwrapper/>

Por enquanto é só, um abraço a todos.
