Title: Django - Herança, Modelos Abstratos e OO Na Veia
Date: 2011-12-15 11:50
Author: arruda
Category: Django, programação, Python, Selecionados, Web
Tags: abstract, abstrato, Django, heranca, heranca multipla, model, modelo, OO, related_name
Slug: django-heranca-modelos-abstratos-e-oo-na-veia
Status: published
Attachments: wp-content/uploads/2011/12/django.png, wp-content/uploads/2011/12/django-structurer.png

Uma coisa que percebi a algum tempo, é que existem poucas referencias à isso nos tutoriais de modo geral, e que usar os conceitos de OO em Django ajudam, e muito, quando seus módulos começam a ficar meio "repetido".  
Felizmente depois de começar a trabalhar na [SparkIt](http://www.sparkit.com.br/), meu colega [Victor Fontes](http://victorfontes.com/) me deu umas dicas de como fazer isso sem problemas. E gostaria de compartilhar isso com vocês.

Herança
-------

<p>

Segue a um cenario de exemplo:  
No exemplo a seguir vemos duas classes, A e B que tem um campo em comum: Nome.  

<script src="https://gist.github.com/1481088.js?file=exemplo_sem_heranca.py"></script>

  
**Problemas:**

</p>

-   Rescrever Codigo:
-   Manutenção:

<p>

Então vemos de cara que podemos usar o conceito mais basico de OO: Herança.  
Vamos criar uma classe pai C que ira **Generalizar** A e B:  

<script src="https://gist.github.com/1481088.js?file=exemplo_heranca.py"></script>

  
**Vantagens:**

</p>

-   Reutilização de Codigo:
-   Manutenção:

**Problemas:**  
Os models são classes que são persistidas em bancos de dados, correto?  
Aí, entra o problema.

No banco de dados as tabelas ficaram(mais ou menos) da seguinte forma:  
**A(id\_c,atributo\_a)  
B(id\_c,atributo\_b)  
C(id, nome)**

Isso é, se fizermos uma consulta:  
*A.objects.get(nome="Arruda")*  
O django ira fazer um **Join** de **A + C** para poder pegar o atributo **Nome** de **A**.  
E isso irá fazer com que suas consultas mais simples se tornem muito pesadas.(Imagine um join numa tabela C que tem os nomes de todos os dados de 20 classes diferentes... é bastante coisa né).  
Logo ficamos desencorajados a usar Herança como deve ser usada.

Mas, existe uma solução:

Modelos Abstratos
-----------------

<p>

No Django é possivel definir um model como sendo abstrato, isso é: **Não é persistido no banco de dados.**  
O exemplo anterior ficaria da seguinte forma(fazendo a **classe C como Abstrata**):  

<script src="https://gist.github.com/1481088.js?file=exemplo_abs_heranca.py"></script>

  
**Vantagens:**

</p>

-   Sem Joins:
-   Além de todas as vantagens de usar Herança.

Isso é algo que permite uma grande variadade de coisas, ainda mais quando usamos Herança Múltipla.

Herança Múltipla
----------------

<p>

Vamos incrementar o exemplo, vamos supor que tanto A quanto B tenham chave estrangeira para uma classe D.  
Com isso podemos criar uma classe F que faca essa ligação:  

<script src="https://gist.github.com/1481088.js?file=exemplo_abs_heranca_multipla.py"></script>

  
Com isso, nossas classes A e B ambas tem os campos Nome e uma chave estrangeira para D.

</p>
<p>

**Mas pera ai!** E se eu quiser definir um related\_name?  
Nesse caso fazemos um pequeno ajuste na classe F:  

<script src="https://gist.github.com/1481088.js?file=exemplo_abs_heranca_multipla2.py"></script>

  
Com essa alteração fazemos com que de **F** possamos **acessar B** da seguinte forma:  

<script src="https://gist.github.com/1481088.js?file=acessar_f_related_names.py"></script>
</p>

**Um abraço, e desejo a todos:  
Que todos tenham prósperos projeto,  
Que seus testes funcionem,  
Que programem bastante e se divirtam nessas ferias.**

Ah sim, e um feliz ano novo e feliz natal... essas trivialidades de sempre...
