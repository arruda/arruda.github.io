Title: Django - Models e métodos dinâmicos usando "templates"
Date: 2012-05-27 18:20
Author: arruda
Category: Django, programação, Python
Tags: Django, exec, format, meta, metaprogramming, programação, python, template
Slug: django-models-e-metodos-dinamicos-usando-templates
Status: published

Quando comecei a pesquisar sobre classes e métodos dinâmicos em Python foi que eu tive essa sacada.  
Para os que não estão familiarizados com o conceito, uma classe dinâmica ou um método dinâmico são basicamente aqueles que você não escreve o código fonte mão, mas sim faz um programa que gera eles para você, tudo isso parte de um conceito chamado **"Meta Programming"**.

O depois de alguns testes eu tive uma certa dificuldade em fazer tais classes, e para o que eu queria, tal dificuldade não fazia sentido.

Então eu vi que existe(de certa forma) outra maneira de fazer tais classes dinâmicas usando métodos como String Format e Exec.

Como Funciona
=============

<p>

O primeiro passo é fazer uma string que contenha o "template" das classes que deveram ser geradas dinamicamente:  

<script src="https://gist.github.com/2815002.js?file=template.py"></script>
</p>
<p>

Em seguida devemos criar uma fabrica de models que usando o template ira retornar o código de uma classe trocando certos pontos chave do template por outros passados como parametro para a fabrica:  

<script src="https://gist.github.com/2815002.js?file=fabric.py"></script>

  
Como pode se ver, nos criamos um dicionario da formatação da string, isso é o que vamos trocar pelo o que, no caso:

</p>

-   Onde tem **CLASS\_NAME** trocamos pelo parametro **name** captalizado(com a primeira letra maiúscula);
-   **CLASS\_DESC** pelo parametro **desc**;
-   **FIELD\_NAME** pelo parâmetro **field**;

Assim o retorno dessa função é uma string que representa o **código** de uma classe com base nos parametros passados para a função fabric.

<p>

Agora que temos nosso template de model e nossa fabrica podemos usa-la para gerar nossas classes dinamicamente, como por exemplo:  

<script src="https://gist.github.com/2815002.js?file=models.py"></script>

  
Nesse trecho de código temos primeiro uma lista(**MY\_MODELS\_LIST**) que define quais são os models que teremos na nossa aplicação.  
E em seguida fazemos um loop por cada elemento dessa lista, e chamamos a factory para os dados de cada um deles.  
Com isso nos temos em cada iteração o **código** de cada Model.  
A string que representa esse código é então executada(usando o método **exec**) e isso faz que o código fonte que estava contido nessa string seja executado =).  
Assim a cada iteração é executado o código de um Model.

</p>

A principio como só é carregado isso na primeira vez que é chamado a classe então não teria um problema de performance tão grande, e é uma boa alternativa para a metaprogramação do Python, por mais que seja mais restrita é mais simples.

É isso, quem quiser ter uma ideia melhor eu fiz um projeto no GitHub que implementa isso: <https://github.com/arruda/django_dynamic_models_test>. Fiquem a vontade para forkar e enviar suas alterações =).

Abraços.
