Title: Preparando o Ambiente de Trabalho - Play
Date: 2011-10-10 10:30
Author: arruda
Category: Ambiente de Trabalho, Java, programação, Web
Tags: ambiente, framework, Java, play, preparando, programação, simples, trabalho
Slug: preparando-o-ambiente-de-trabalho-play
Status: published

Graças ao pedido do [Fabio C. B.](http://www.arruda.blog.br/programacao/preparando-o-ambiente-de-trabalho-flask/#comment-101) que conheci essa fantástica framework web conhecida como Play.

Sem mais enrolação(vou fazer um post com mais detalhes nessa framework), vamos ao que interessa:

Preparando o Ambiente
---------------------

Vale ressaltar que estou considerando a instalação em um Ubuntu 11.04.

### JDK e JRE

Para instalar o play é preciso ter o JDK, para isso rode:

``` {lang="bash"}
$ apt-cache search jdk
$ apt-get install sun-java6-jdk sun-java6-jre
```

Isso deverá instalar o JDK e JRE no seu Ubuntu.

Instalando a Framework
----------------------

Baixe a última versão do play no site <http://www.playframework.org/download>  
Deszipe o conteúdo para uma pasta, ex: **"/home/MeuUser/play"**

### Variáveis de Ambiente

Abra seu arquivo **.bash\_rc** e adicione ao final deste:

``` {lang="bash"}
export PLAY_HOME=/home/MeuUser/play
PATH=$PATH:/home/MeuUser/play
export PATH
```

**Assim você poderá usar o comando "play" de qualquer local.**

Usando IDEs
-----------

### Eclipse

Para usar o play no Eclipse basta usar o comando:

``` {lang="bash"}
$ play eclipsify myApp
```

E importar o projeto para seu workspace  
Para mais informações tem o link do proprio Play mostrando como configurar os detalhes: [Play in Eclipse](http://www.playframework.org/documentation/1.2.3/ide#eclipse)

### NetBeans

Para usar o play no NetBeans basta usar o comando:

``` {lang="bash"}
$ play netbeansify myApp
```

E abrir o app como um projeto NetBeans.  
Para mais informações tem o link do proprio Play mostrando como configurar os detalhes: [Play in NetBeans](http://www.playframework.org/documentation/1.2.3/ide#netbeans)

Versionamento
-------------

Ao incluir um projeto em um controle de versionamento, lembre-se de mandar ignorar as pastas necessarias.  
Um exemplo do .gitignore(caso esteja usando GIT) é:

``` {lang="bash"}
/tmp
/modules
/lib
/test-result
/logs
```

  

Isso é tudo, espero que tenha ajudado a vocês, e muito obrigado pela dica do [Fabio C. B.](http://www.arruda.blog.br/programacao/preparando-o-ambiente-de-trabalho-flask/#comment-101) de fazer o próximo post sobre essa framework incrível.

Fiquem ligados para mais posts dessa serie, e façam como o Fabio:  
Caso tenham alguma sugestão podem mandar nos comentários que eu ficarei feliz eu dar uma olhada.
