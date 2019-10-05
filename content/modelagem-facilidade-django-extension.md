Title: Usando Django Extensions
Date: 2011-04-06 01:28
Author: arruda
Category: Django, programação
Tags: Django, django-extensions, extensions
Slug: modelagem-facilidade-django-extension
Status: published

### O que posso falar desse projeto?

Talvez que o nome dele deveria ser **Django-Essentials**, pois possui diversas app extremamente uteis e importantes para a maioria dos projetos em Django.

Mas devo admitir que o que me deixou mais boquiaberto foi a introdução do comando **graph\_models**. Esse singelo comando não faz nada mais, nada menos, que gerar um diagrama UML da estrutura de dados do seu BD, apenas baseando-se nos models das suas aplicações.

### Parece pouco? Pois aí você se engana!

Já utilizei umas 3 ferramentas do mesmo tipo(Engenharia reversa do banco de dados para gerar a UML) em Java, porém TODAS elas(a maioria paga) sempre deram resultados confusos e embaraçados, acabou que depois de usar as ferramentas, foi preciso um bom tempo pra arrumar os desenhos para não ficarem um em cima do outro.

O graph\_models por outro lado, gera tudo organizado e limpo que é uma beleza, ele permite até mesmo a opção de agrupar por apps, criando grandes blocos para cada um. Resumindo, ele faz um ótimo trabalho, bonito e o melhor de **GRAÇA**!

### Isso não é tudo!

As vantagens do Django-Extensions(ou Django-command-extenssions), não param por ai:

-   export\_emails: exporta todos os emails do seu banco de dados para um formato conhecido(Outlook, Gmail, etc...)
-   create\_app: cria uma estrutura de diretórios para o nome da app em questão. Além disso, permite criar diretórios de template para a mesma app.
-   runserver\_plus: Uma versão tunada do comando, que executa usando um servidor de debug Werkzeug que simplesmente faz magica!
-   AutoSlugField: Um campo de slug automatico para seus models.
-   E muito mais!

Como instalar:
--------------

Baixe a ultima versão do repositório do gitHub:  
<http://github.com/django-extensions/django-extensions/tarball/master>

Extraia o conteúdo e instale:  
\$python setup.py install

Coloque a aplicação no "INSTALLED\_APPS" do seu settings.py:  
INSTALLED\_APPS = (  
…  
‘django\_extensions’,  
)

Assim seu projeto já pode usar o django\_extensions.

Apenas alguns detalhes:
-----------------------

Para usar o comando graph\_models, você deve instalar graphviz e pygraphviz:  
\$sudo apt-get install graphviz-dev  
\$sudo apt-get install python-pygraphviz

Para usar o runserver\_plus é preciso instalar o Werkzeug na sua maquina, isso é tao simples quanto:  
\$sudo easy\_install Werkzeug
