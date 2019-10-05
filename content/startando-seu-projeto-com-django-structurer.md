Title: Startando Seu Projeto com Django Structurer
Date: 2011-11-16 09:21
Author: arruda
Category: Ambiente de Trabalho, Django, programação, Python, Selecionados, Web
Tags: Django, facil, organizado, projeto, start, struct, structurer
Slug: startando-seu-projeto-com-django-structurer
Status: published
Attachments: wp-content/uploads/2011/11/folder_struct2.png

Gostaria de apresentar essa app que fiz a pouco tempo(e que ainda estou desenvolvendo) para facilitar e agilizar o desenvolvimento do seu projeto Django de forma mais padronizada e modularizada: **Django Structurer**

Instalando
----------

Depois de muita dor de cabeça, consegui fazer com que essa app seja instalada facilmente usando o pip, então é a penas fazer:

``` {lang="bash"}
pip install django-structurer
```

Usabilidade Básica
------------------

``` {lang="bash"}
djstruct.py proj "meuProjeto"
```

Ao executar esse comando, um projeto django é criado na pasta em que o usuário usou o comando.

Estrutura Básica Padrão
-----------------------

A estrutura básica que o projeto é criado, foi feita pensando em diversos detalhes para a modularização de todo o projeto e para deixar de forma mais organizada, assim facilita o entendimento para novos integrantes no projeto e outros detalhes.  
Segue uma imagem de como ficaria o projeto gerado com o comando anterior:  
[![Estrutura do Projeto]({static}wp-content/uploads/2011/11/folder_struct2.png "folder_struct"){.alignnone .size-full .wp-image-862 width="328" height="534"}]({static}wp-content/uploads/2011/11/folder_struct2.png)

Personalizando a Estrutura De Projetos
--------------------------------------

Muitos vão dizer:  
"Mas Arruda, na minha empresa a gente não usa esse padrão não, usamos um pouco diferente, como faço?"

Pensando nisso, já provi a solução:  
O Django Structurer permite uma total personalização da estrutura a ser usada.  
Para criar sua própria configuração é preciso a penas fazer um arquivo no formato YAML descrevendo como você quer sua organização.  
Segue um exemplo de um possível conteúdo do arquivo YAML:

### Exemplo de Configuração

Abaixo mostrarei um trecho de um arquivo de configuração, e irei explicar qual a estrutura de diretórios que ele gera:

``` {lang="bash"}
name: $project_name
archives:  
- name: pasta1
  archives: []
  
- name: pasta2
  archives:
  - name: arquivo.txt

- name: $project_name
  archives:  
  - name: __init__.py

  - name: manage.py
    snippets: [default.manage.full]
...
```

Isso irá fazer uma estrutura de arquivos desse tipo:

``` {lang="bash"}
|meu_projeto
|----pasta1
|----pasta2
      |----arquivo.txt
|----meu_projeto
      |----__init__.py
      |----manage.py
...
```

Onde tem escrito **\$project\_name** será substituído pelo nome do projeto que está sendo criado.  
Para fazer uma pasta basta por descrever novos arquivos dentro da parte **archives**.  
Para por um arquivo, basta não por o atributo **archives**.  
Simples assim.

Snippets
--------

"Ok, as pastas estão agora no meu padrão, mas os arquivos não tem o conteúdo que eu costumo por em minha empresa. \#comufas ?"

Para customizar o conteúdo de um arquivo é simples, basta usar os snippets já prontos do Django Struct ou fazer os seus proprios.

### Mas o que são Snippets

Snippets são trechos de código, texto ou dados serializados.  
No exemplo anterior, o arquivo manage.py tem o conteúdo completo de um arquivo manage.py normal, isso foi definido quando fizemos:

``` {lang="bash"}
- name: manage.py
    snippets: [default.manage.full]
```

Um outro exemplo de snippets que pode ser utilizado é o cabeçalho contendo a codificação de um arquivo python

``` {lang="bash"}
#-*- coding:utf-8 -*-
```

Para fazer isso basta adicionar um outro snippet antes do citado: **default.general.header**.  
Ficando assim:

``` {lang="bash"}
- name: manage.py
    snippets: [default.general.header, default.manage.full]
```

**OBS: Lembrando que a ordem em que são escritos os snippets são a ordem em que eles serão escritos**

Configuração Para Personalizar
------------------------------

"Ok, eu posso usar diferentes snippets, mas e se eu quiser usar meus proprios snippets, como faço?"

Para usar diferentes snippets basta criar uma pasta em que você ira salvar seus snippets, ex:

``` {lang="bash"}
mkdir ~/.myStructs
```

e criar no .bashrc para ter o seu DJSTRUCT\_HOME nas variáveis de ambiente:

``` {lang="bash"}
export DJSTRUCT_HOME=/home/usuario/.myStructs
```

Dentro da sua pasta ".myStructs" crie uma pasta "Snippets", e dentro dela coloque seus arquivos, lembrando de por a terminação ".snippets".  
Então se você quer por um novo snippet com imports que costuma usar sempre, você pode por eles num arquivo: "imports\_importantes.snippets" dentro da pasta ".myStructs/Snippets".

Pronto, seu snippet já pode ser usado.  
Para chamar ele nas configurações do seu projeto, basta por no atributo "snippets":

``` {lang="bash"}
[imports_importantes, uma_pasta.outro_snippet]
```

Como usar sua própria configuração
----------------------------------

Para usar o seu próprio arquivo de configuração(o arquivo YAML com a organização do projeto) você usa o comando da seguinte forma:

``` {lang="bash"}
djstruct.py proj "meu_projeto" MinhasConfiguracoes.yaml
```

Isso é o terceiro parâmetro é o arquivo de configuração que será usado.  
Sendo que você pode por o seu arquivo de configuração dentro de seu DJSTRUCT\_HOME, para acessar facilmente o mesmo.

### Usando uma Configuração por Default

Você pode deixar uma configuração como sendo a padrão setando uma outra variável de ambiente:

``` {lang="bash"}
DJSTRUCT_DEFAULT = /home/usuario/.myStructs/MinhasConfiguracoes.yaml
```

Assim você pode usar o comando sem ter que passar qual a configuração que por default ele ira carregar a indicada:

``` {lang="bash"}
djstruct.py proj "meuProjeto"
```

Quer ajudar?
------------

Gostaria de ajudar? Dar alguma dica, ou disponibilizar sua própria configuração/snippets?  
Faça um fork do projeto no github: <https://github.com/arruda/django-structurer> e contribua para tornar essa uma ferramenta melhor.

Isso é tudo, espero que isso ajude bastante pessoas a desenvolverem e iniciarem seus projetos mais rapidamente de maneira mais organizada.
