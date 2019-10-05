Title: Adicionando um widget no seu formfield, usando inlineformset_factory
Date: 2012-02-06 17:55
Author: arruda
Category: Django, programação, Python, Selecionados, Web
Tags: add, adicionar, Django, factory, form, formfield, inline, inlineformset_factory, widget
Slug: adicionando-um-widget-no-seu-formfield-usando-inlineformset_factory
Status: published

Para começar com o pé direito aqui na Campus Party estou fazendo esse post com uma informação que pode ser bastante útil para outros.

O Problema
----------

Estava usando inlineformset\_factory para colocar varios arquivos de uplaod que estavam ligados a um model ai, mas o problema mesmo foi que eu queria que cada um dos **'inlines'** tivesse um widget no campo de FileField.  
Depois de muuuuito bater a cabeça, e de olhar a fundo o fonte do Django(graças a facilidade da IDE Eclipse como descrevi **[nesse post](http://www.arruda.blog.br/programacao/review-eclipse-django-virtualenv/ "Eclipse ta legal")**) eu descobri uma maneira de fazer isso sem ter que sair herdando e alterando tudo quanto é classe por aí.

Solução
-------

<p>

Primeiramente você deve criar seu próprio método para o formfield\_callback.  
Nesse método você pega qual o formfield do campo passado no parâmetro e altera o widget do mesmo para o que você precisa, e em seguida retorna o formfield alterado. Vou mostrar o exemplo do meu caso, em que alterei o widget para usar o meu widget nos FileFields:  

<script src="https://gist.github.com/1754686.js?file=my_formfield_utils.py"></script>
</p>
<p>

Em seguida na sua view onde você usa o seu inlineformset\_factory você altera a chamada do método para usar o seu método como formfield\_callback, ex:  

<script src="https://gist.github.com/1754686.js?file=my_nice_view.py"></script>
</p>

E isso deve ser o suficiente.

<p>

Caso seja útil para mais alguém o widget que eu fiz retira o caminho completo do arquivo de um campo de upload e retira o link do mesmo, deixando apenas o nome do arquivo.  
No meu caso era interessante o mesmo para não deixar claro para os usuários do sistema qual era a estruturação de pasta do meu sistema, e como não havia a necessidade do usuário reaver o arquivo enviado não era necessário nem o link nem o caminho completo para o mesmo(deixei apenas o nome do arquivo assim o usuário sabe qual o arquivo que ele enviou pelo nome). Segue o código do mesmo:  

<script src="https://gist.github.com/1754686.js?file=my_widget.py"></script>
</p>

Isso é tudo, abraços!
