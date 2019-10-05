Title: JayFlot - Integração Flot e Java Web
Date: 2011-09-01 10:51
Author: arruda
Category: Java, programação, Selecionados, Web
Tags: download, exemplo, facil, flot, integracao, Java, jayflot, plot, plotagem, web
Slug: jayflot-integracao-flot-e-java-web
Status: published
Attachments: wp-content/uploads/2011/09/flot-example.png

Quem nunca pensou em usar um ou mais gráficos em sua app Java Web?  
Para fazer em desktop existem várias bibliotecas que permitem tal proeza, mas quando vamos para web... Aí é outra história, e pelo que pesquisei, a única forma de fazer gráficos sem dor de cabeça é usando o [Flot](http://code.google.com/p/flot/).

O Problema
----------

O que pode dificultar a utilização do Flot é que é preciso fazer uma série de métodos para serializar os dados que se quer para gerar o dicionário de dados em JS.  
Isso, além de cansativo é repetitivo. Foi aí que tive a idéia de fazer uma biblioteca Java para lidar com isso, seu nome é **JayFlot**.

JayFlot
-------

Essa biblioteca permite uma fácil serializacao, além de ter métodos que facilitam a criação de gráficos internamente.  
E o melhor de tudo é que pode ser usado em praticamente qualquer framework web de Java.

Exemplo
-------

Vamos supor que esteja usando **JSF** e sua app seja uma loja virtual, e queira fazer um grafico com informações de **vendas** e **custo** de um produto por **período**.

### 1º Passo

Inclua no seu projeto as bibliotecas **jayflot-0.1.jar** e **gson-1.7.1.jar**.  
Agora você já pode usar o jayflot

### 2º Passo

No service faça um método para gerar os dados do grafico(usando um ArrayList da classe PlotData). Lembrando, de fazer o import das classes **Plot** e **PlotData**.  
Ex:

``` {lang="java" line="1"}
public ArrayList gerarPlotDataDeCustoEVendasPorPeriodo(List periodos, List vendas, List custos){
     ArrayList datas = ArrayList();
     //o primeiro parâmetro do método é o eixo X e o segundo o eixo Y
     PlotData vendasData = Plot.generatePlotData(periodos,vendas);
     vendasData.setLabel("Vendas");
     datas.add(vendasData);

     PlotData custosData = Plot.generatePlotData(periodos,custos);
     custosData.setLabel("Custos");
     datas.add(custosData);
     return datas;
} 
```

### 3º Passo

Ainda no service faça um outro método para gerar o grafico(uma instancia da classe **Plot**) usando os dados populados no método anterior:  
Ex:

``` {lang="java" line="1"}
public Plot gerarPlotDeCustoEVendasPorPeriodo(List periodos, List vendas, List custos){
     //chama o metodo anterior para gerar o ArrayList de PlotData.
     ArrayList datas = this.gerarPlotDataDeCustoEVendasPorPeriodo(periodos,vendas,custos);

     //os parametros sao: Lista das PlotDatas desse grafico, Label do Eixo X e Label do Eixo Y.
     Plot grafico = Plot.generatePlot(datas,"Periodos De Produção","R$");
     return grafico;
} 
```

### 4º Passo

No seu manageBean faça uma instancia de um **Plot** que será seu grafico, e faça ele receber o retorno do seu metodo criado no service. E não esqueça dos métodos **Get e Set** para ele!  
Ex:

``` {lang="java"}
private Plot graficoVendasCustosPeriodo;
....
public String mostrarGraficoVendasECustosPorPeriodo(){
     //considerando que em algum momento você já populou os vetores de periodos, vendas e custos
     graficoVendasCustosPeriodo = meuService.gerarPlotDeCustoEVendasPorPeriodo(periodos,vendas,custos);
     return PAGINA_GRAFICO;
} 
```

### 5º Passo

Faça a sua tela de grafico, quando for fazer o JS, faça algo do tipo:

``` {lang="javascript"}
data = [];
data = #{myBean.graficoVendasCustosPeriodo.printData};
...
options = {};
options = #{myBean.graficoVendasCustosPeriodo.printOptions};
....
$j.plot($j("#placeholder"), data, options);
...
```

Dessa forma onde teriam que ter as informações de data e options no Flot ele irá imprimir os dados do seu gráfico que está no bean.  
**Ou você pode usar a tag JSF que eu fiz: [JayFlot\_CheckBoxTag\_JSF](https://gist.github.com/78453a5a55fc63284126)**

### Pronto, seu gráfico está feito!

Sem dor de cabeça, sem ter que ficar gerando json, ou concatenando strings, nem nada. Só chamar os métodos do Plot e setar algumas informações.

Onde Baixar?
------------

Quem quiser pode fazer o download da biblioteca, os fontes se encontram no GitHub: [http://arruda.github.com/JayFlot](http://arruda.github.com/JayFlot/).

Um abraço a todos.
