Title: Aplicativos Uteis Para Java
Date: 2011-06-06 12:34
Author: arruda
Category: Java, programação
Tags: aplicativos, Eclipse, IDE, Java, javadocs, jdk, jre, netbeans, uteis, versionamento
Slug: aplicativos-uteis-para-java
Status: published

Segue agora um conjunto de aplicativos que acho que são muito bons para aqueles que estão desenvolvendo em Java, e algumas dicas:

Antes de mais nada...
---------------------

O essencial para tudo é ter instalado o **[JDK](http://www.oracle.com/technetwork/java/javase/downloads/jdk-6u25-download-346242.html)**, já que sem ele não é possível desenvolver app em Java.  
Lembrando que ao instalar a JDK ele costuma instalar o JRE junto, então sem problemas para executar e testar suas app recem criadas.

IDEs
----

As melhores IDEs do mercado são o Eclipse e o NetBeans.  
Agora quando é melhor usar um, e quando é melhor usar outro?  
**[Eclipse](http://www.eclipse.org/downloads/)**

Roda bem mais leve que o NetBeans, da um pouco mais de trabalho pois não tem tantas coisas automáticas quanto o NetBeans.  
Vale apena usar em projetos web, ou onde não da pra depender muito da automação das tarefas(que acabam zoneando o código com o tempo).  
Não vale apena quando é um projeto desktop(muito mais demorado e sem interface amigável).

**[NetBeans:](http://netbeans.org/downloads/)**

Mais pesado que o Eclipse, mas em compensação tem várias facilidades que o Eclipse não traz(ambos possuem auto-complete =D).  
Pode ser usado sim para web, sem problemas, mas para um projeto mais robusto eu prefiro não utilizar algumas das opções de gerar os .xmls automaticamente, pois acabam ficando meio loucos com o crescimento da sua app.  
Perfeito para aplicativos desktop, porem a parte de interface amigável pode acabar prendendo você um pouco, o melhor nessas horas é pegar apenas o modelo inicial do netBeans, para depois por a mão na massa.

Versionamento
-------------

Para o Eclipse temos o pluging para versionamento com SVN, o **Subversive**.  
Para instalar o mesmo, tem o passo-a-passo no site do eclipse: [Instalando Subversive](http://www.eclipse.org/subversive/documentation/gettingStarted/aboutSubversive/install.php)

Já para o NetBeans o plugging para SVN embutida na IDE funciona apenas para usuarios windows(WTF?!), os outros OS precisam baixar um cliente svn para poder fazer o mesmo. Também tem um tutorial ensinando como fazer isso, aqui: [Subversion On NetBeans](http://netbeans.org/kb/docs/ide/subversion.html)

JavaDocs
--------

Para quem gosta de ver como funcionam os códigos que estão usando ou querem pegar referencia de como é feito o que como e por que, eu aconselho usar o JavaDoc. A principio o JavaDoc já vem com seu JKD.  
Caso não esteja conseguindo abrir ou encontrar seu javaDoc, não se desespere: [www.javadocs.org](http://www.javadocs.org) é o site que tem o javadoc online.

Java Decompiler
---------------

Se você quer descompilar um ".class" para saber como ele foi implementado e ter os ".java" em mãos, recomendo esses aplicativos:  
**[Jad](http://www.varaneckas.com/jad)**

Esse Aplicativo descompila o java, foi um dos originais, o problema é que não é atualizado a muito tempo.

**[DJ Java Decompiler](http://ziggi.uol.com.br/downloads/java_decompiler)**

Muito bom esse, porém é apenas free por um periodo curto de tempo, depois é pago.

OBS: Estou considerando como IDEs:  
**NetBeans Java EE  
Eclipse IDE for Java EE Developers**

É isso, um abraço para todos.
