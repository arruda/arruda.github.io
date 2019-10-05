Title: Fazendo um MakeFile
Date: 2011-11-28 12:27
Author: arruda
Category: C/C++, programação
Tags: C, CPP, example, exemplo, make, makefile
Slug: fazendo-um-makefile
Status: published

Então, depois de quebrar um pouco a cabeça com um projeto que estou fazendo, decidi compartilhar essa informação aqui com vocês, caso isso venha a ser útil para mais alguém.

Considerações
=============

Fiz esse makefile pensando numa maneira bem genérica, já que minha app tem que gerar um makefile para compilar umas questões em c++.  
Dessa forma o makefile pode ser usado em apps não muito sofisticadas(sem divisão de diretórios para headers e src por exemplo) que funciona direitinho(testado diversos casos ;) ).

O Arquivo
---------

``` {lang="bash"}
CC=g++
CFLAGS=-c -Wall
LDFLAGS=
SOURCES= fontes/main.cpp fontes/hello_world.h 
OBJECTS=$(SOURCES:.cpp=.o)
EXECUTABLE= exec/hello_world
all: $(SOURCES) $(EXECUTABLE)
$(EXECUTABLE): $(OBJECTS)
    $(CC) $(LDFLAGS) $(OBJECTS) -o $@
.cpp.o:
    $(CC) $(CFLAGS) $< -o $@
clean:
    rm -rf fontes/*.o
```

Nesse exemplo temos uma **main.cpp** e um header **hello\_world.h** e isso será compilado e irá gerar um executável **hello\_world**.

Basicamente é isso.  
Onde tem

``` {lang="bash"}
SOURCES=
```

você lista seus arquivos fontes, e onde tem

``` {lang="bash"}
EXECUTABLE=
```

é o executável a ser gerado.  
E por fim é feita uma remoção dos arquivos **.o** da pasta **fontes/**

Espero que isso tenha ajudado, e uma imagem que eu fiz acerca de makefiles:  
[![MAKEFILE make your self!](http://d24w6bsrhbeh9d.cloudfront.net/photo/744366_700b.jpg "MAKEFILE make your self!"){.alignnone width="498" height="414"}](http://9gag.com/gag/744366)
