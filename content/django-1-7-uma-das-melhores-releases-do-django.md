Title: Django 1.7 - Uma das melhores releases do Django?
Date: 2014-01-13 10:23
Author: arruda
Category: Django, programação, Python, Selecionados, Web
Tags: 1.7, Django, melhor, notas, notes, release
Slug: django-1-7-uma-das-melhores-releases-do-django
Status: published
Attachments: wp-content/uploads/2014/01/djang_17.jpg

Para quem ainda não sabe a nova versão do Django (a versão **1.7**) em data de lançamento prevista para **16 de Maio** deste ano.

"E dai?" vocês devem estar perguntando... Bem, "e dai" que essa nova versão tem diversas novas funcionalidades que por mim é uma das **melhores** (se não a melhor) releases do Django até agora. Eis os porquês:  
\[adsense\]

Schema Migration
----------------

Por mim essa é a principal novidade.  
Finalmente o Core do Django decidiu investir, com uma abordagem muito interessante ([um projeto no kickstarter](http://www.kickstarter.com/projects/andrewgodwin/schema-migrations-for-django "Schema Migration do Django no Kickstarter")), e agora o Django terá uma App de Schema Migration embutida e pronta para ser usada =D.

Basicamente o [Andrew Godwin](http://www.aeracode.org/ "Página do Andrew Godwin") fez essa app baseada no [Django South](http://south.aeracode.org/ "Django South Page") com algumas melhorias.

Para quem não entendeu ainda qual as vantagens, basta exemplificar com um dos principais problemas (que qualquer um que já tenha feito algum projeto em Django já deve ter tido), que é poder "atualizar" as tabelas do banco de dados...

Isso por que, o agora depreciado, **"syncdb"** apenas criava tabelas novas **caso elas não existissem**, mas **não atualizava** caso os campos desta fossem alterados.

[Mais informações sobre essa feature](https://docs.djangoproject.com/en/dev/releases/1.7/#schema-migrations "Schema migrations no Django 1.7").

App Loading Refactor
--------------------

Houve uma **grande refatoração** na parte do carregamento das apps, coisas que facilitam muito a vida do desenvolvedor, como:

-   Apps podem rodar código durante o startup, antes que o Django execute qualquer coisa;
-   Chega de ficar explicitando app\_label no seus models caso eles fiquem fora do padrão "models.py", agora seus models são achados automaticamente sem ter que setar nada;
-   É possível ter uma app sem ter um "models.py" caso essa não possua models

[Mais informações sobre essa feature](https://docs.djangoproject.com/en/dev/releases/1.7/#app-loading-refactor "App Loading Refactor no Django 1.7").

Formulários
-----------

### Form.add\_error

Com essa nova funcionalidade é possível incluir um erro para algum campo específico de dentro do método "**Form.clean()**".  
Basicamente você passa como primeiro parâmetro uma string que tem o nome do campo (string vazia é considerado como um erro genérico do formulário) e como segundo parâmetro um **ValidationError** com a mensagem que preferir.

[Mais informações sobre essa feature](https://docs.djangoproject.com/en/dev/ref/forms/api/#django.forms.Form.add_error "Form.add_error no Django 1.7").

### Form.errors.as\_json

Bem, já era hora né?  
Para quem já brincou com ajax sabe que é um porre toda vez ter que serializar os erros para Json.  
Agora não precisa mais se preocupar com isso, basta chamar esse método que ele retorna pra você tudo bonito.

[Mais informações sobre essa feature](https://docs.djangoproject.com/en/dev/ref/forms/api/#django.forms.Form.errors.as_json "Form.errors.as_json no Django 1.7").

Custom Manager para Reverse Relations
-------------------------------------

Agora é possível explicitar um Custom Manager para uma relação reversa:  
Por exemplo:

``` {lang="python"}
from django.db import models

class Entry(models.Model):
    #...
    objects = models.Manager() # Default Manager
    entries = EntryManager() # Custom Manager

>>> b = Blog.objects.get(id=1)
>>> b.entry_set(manager='entries').all()
```

Isso é muito bacana pra quem conhece as vantagens de usar Managers customizados mas não conseguia usar para esse caso específico.

[Mais informações sobre essa feature](https://docs.djangoproject.com/en/dev/releases/1.7/#using-a-custom-manager-when-traversing-reverse-relations "Using a custom manager when traversing reverse relations no Django 1.7").

Tchau Memoize
-------------

Para quem usava o **Memoize** (django.utils.functional.memoize), fiquem atentos pois ele vai ser depreciado nessa versão (em troca do lru\_cache).  
Na versão 1.9 Memoize vai embora, então é bom fazer a troca o quanto antes.

Bem, essas são as razões deu achar essa release fantástica.  
E você o que acha? Prefere alguma outra release? Qual? E por que?

Abraços.
