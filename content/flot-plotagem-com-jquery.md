Title: Flot - Plotagem com JQuery
Date: 2011-06-01 12:10
Author: arruda
Category: programação, Web
Tags: flot, grafico, javascript, jquery, js, plot, plotagem
Slug: flot-plotagem-com-jquery
Status: published

Esse otimo plugin para JQuery permite fáceis e maravilhosos gráficos!

Estive nos últimos dias utilizando no trabalho um plugin muito bacana de JQuery, o **Flot**.  
Esse plugin trata-se de gráficos (Plotagem) usando JS. De forma que fica muito bonito a aparência final, mas sem perder a funcionalidade(tem diversas opções configuraveis).

<p>

Exemplo:  

<script src="wp-content/scripts/flot/jquery.js" type="text/javascript"></script>

  

<script src="wp-content/scripts/flot/jquery.flot.js" type="text/javascript"></script>

  

<script src="wp-content/scripts/flot/exemploFlotBasic.js" type="text/javascript"></script>
</p>

::: {#placeholder style="width:600px;height:300px;"}
:::

Código JS:

``` {lang="JavaScript" line="1"}
$(function () {
    var d1 = [];
    for (var i = 0; i < 14; i += 0.5)
        d1.push([i, Math.sin(i)]);

    var d2 = [[0, 3], [4, 8], [8, 5], [9, 13]];

    // um null significa um segmento separado
    var d3 = [[0, 12], [7, 12], null, [7, 2.5], [12, 2.5]];

    $.plot($("#placeholder"), [ d1, d2, d3 ]);
});
```

E no html basta por no body:

``` {lang="html"}
```

  
  
O código do Flot está num repositório no [GitHub](https://github.com/flot/flot) com uma significante colaboração da comunidade. Existem ainda alguns pequenos bugs, mas nada muito complicado de ser arrumado(Alguns repositórios, o meu inclusive, já estão com algumas alterações para isso).  
Creio que o que falta agora para esse incrivel plugin seja uma parte de **Grafico 3D**(e ai [Zeno](http://blog.zenorocha.com/) e Zanoni, afim de forkar?)  
Basicamente é isso o que tinha a dizer, para quem quiser saber mais, basta entrar na página do projeto: [Flot](http://code.google.com/p/flot/)

**OBS:** Estou tentando fazer um app de Django para facilitar o uso do Flot em projetos, assim o programador não precisa lidar com códigos em javascript que nem um louco, ele popula o grafico internamente e só utiliza a tag necessária no template. Quem estiver afim de ajudar é so fazer um fork também: [DjangoFlot](https://arruda@github.com/arruda/DjangoFlot)

Abraço.
