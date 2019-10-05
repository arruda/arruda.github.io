Title: Django - Instalar com Brew, apt-get ou PIP?
Date: 2013-02-05 18:17
Author: arruda
Category: Ambiente de Trabalho, Django, programação, Python, Selecionados, Web
Tags: aptget, brew, Django, instalar, install, pip
Slug: django-instalar-com-brew-apt-get-ou-pip
Status: published

Percebi que algumas pessoas tem tido essa dúvida(obrigado analitics) e acho que é uma boa esclarecer isso.

A minha resposta é: **Use o PIP**.  
Vou explicar exatamente porque essa é uma abordagem muito melhor que usar brew, apt-get ou qualquer outro tipo de solução similar.

VirtualEnv
----------

Para quem não conhece o virtualenv, ele é uma ferramenta que permite trabalhar com ambientes virtuais em python  
(não vou entrar muito nos detalhes, para mais infos sobre isso tem esse [post](http://www.arruda.blog.br/programacao/python/usando-virtualenvwrapper/ "Usando VirtualEnvWrapper")).  
Voltando... o pip e o virtualenv combinam perfeitamente, assim é ridiculamente simples controlar o que está sendo usado no ambiente em questão usando o Pip.  
Já as outras soluções são mais voltadas para instalar pacotes no sistema inteiro, e não são tão facilmente integradas com o virtualenv, isso torna o uso dessas alternativas algo  
\[adsense\]

Dependências (requirements):
----------------------------

O pip possui o recurso de instalar a partir de um arquivo todas as dependências de um projeto python,  
enquanto as outras soluções não possuem um controle das versões e nem todas as dependências disponíveis.

Multi-plataforma
----------------

O pip funciona em linux ou mac ou windows (na média do possível, considerando que é o windows).  
Assim, usando pip fica mais fácil controlar os pacotes do projeto Django, já que em qualquer sistema bastaria usar o mesmo comando do pip.  
Imagina que chato, se você controlar todas as dependências com o apt-get no Ubuntu por exemplo, e depois vai pra um Mac e  
tem que sair pesquisando os pacotes equivalentes usando o brew.

Conclusão
---------

**Prefira sempre o pip a outras soluções...**
