Title: Atalhos Úteis de NetBeans, e outros detalhes.
Date: 2011-04-25 00:02
Author: arruda
Category: Java, programação
Tags: Java, netbeans, pcs, prova
Slug: infos-uteis-para-prova-1-de-pcsnetbeans
Status: published

Decidi fazer um post para ajudar quem for fazer a prova de PCS , são só algumas dicas basicas do netBeans e alguns detalhes de java. Não sei se ajudará muito.

HotKeys
-------

**Ctrl+Shift+i** : Resolver problemas de imports na classe  
**Ctrl+K / Ctrl + L :** Auto-complete melhorado  
**Ctrl + R:** Renomear  
**Ctrl + shit + f:** procurar nos projetos  
**ctrl + e:** deletar linha  
**Alt+shift + f:** formatar código  
psvm -\> cria um método main (public static void main)

Code Templates
--------------

No netBeans escreva o codigo em negrito e aperte tab, ele irá imprimir o texto correspondente:  
**sout** =\> System.out.println("");  
**psvm** =\> public static void main(String\[\] args)  
**fore** =\> foreach pre montado.

**Bom para contruir a classe:**  
**Alt+Insert :** Inserir código(em classes permite atalho para gerar gets e sets, construtores e o que você quiser)

Comandos
--------

**Scanner**, usando o metodo next(ou nextTipoVariavel), para pegar a próxima entrada do tipo desejado, ou apenas a próxima entrada:

``` {lang="JAVA" line="1"}
import java.util.Scanner;
        Scanner scan = new Scanner(System.in);
        String linha = scan.nextLine();
        int inteiro = scan.nextInt();
        double db = scan.nextDouble();
        BigDecimal bigd = scan.nextBigDecimal();
```

Detalhes do **BigDecimal:**

``` {lang="JAVA" line="1"}
import java.math.BigDecimal;

BigDecimal bigD;
//Diferentes modos de instanciar
bigD = new BigDecimal();
bigD = new BigDecimal("0.0");
bigD = new BigDecimal(0.00);
//Soma de BigDecimals
bigD = bigD.add(bigD);
//Divisao de BigDecimals
bigD = bigD.divide(bigD);
//Divisao de BigDecimals
bigD = bigD.divide(bigD);
//Multiplicacao de BigDecimals
bigD = bigD.multiply(bigD);
//Comparacao de BigDecimals, retorno é um inteiro
if (bigD.compareTo(bigD)==0) {
    System.out.println("Igual");
}
```

\[adsense\]

Infos de **String:**

``` {lang="JAVA" line="1"}
String str = "Essa é uma string bem doida. Não é?"

String stringsDivididasPorEspaco [] = str.split(" ");
String stringsDivididasPorPonto [] = str.split(".");

String strComFraseNoFim = str.concat("Frase");

//em comparacao de strings se utilize o metodo equals
if(str.equals("String Diferente")){
    System.out.println("Não será verdadeiro, logo não vai entrar aqui.");
}
```

Ainda estou tentando lembrar como faz no netbeans pra que crie uma classe automaticamente como filha de outra, ou implementando alguma interface(sem ser na mão).  
Mas é isso ai, espero que isso ajude.
