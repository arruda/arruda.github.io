Title: Configurando seu Eclipse para C/C++
Date: 2011-04-02 17:42
Author: arruda
Category: C/C++, programação, Selecionados
Tags: C, CPP, Eclipse, IDE, programação
Slug: configurando-seu-eclipse-para-cc
Status: published

Depois de muito tempo programando em IDEs simplistas como Dev, ou exageradas como microsoft c++, finalmente descobri a IDE que supre todas as minhas necessidades de programação em C/C++:  
**Eclipse**

Para aqueles não familiarizados com o nome (não, não tem nada haver com vampiros que brilham no sol), o Eclipse é uma das melhores IDEs de Java no mercado, junto com Netbeens e outras.  
Mas, indo direto ao que interessa, essa magnífica ferramenta possui certas facilidades como:

-   Auto-completar
-   Simplicidade de uso
-   Roda leve como uma pluma.

Bem, basicamente é como eu digo: "Não programe, deixe que o Eclipse programe por você."

Não vejo muito sentido em ter que escrever todas as linhas de código quando já existem IDEs que são capazes de tal feito.  
\[adsense\]

**Instalação:**
---------------

Para instalar o Eclipse C/C++ na sua maquina, basta fazer o download do programa:  
[Eclipse Galileo C/C++](http://www.eclipse.org/downloads/packages/eclipse-ide-cc-developers/galileosr2 "Eclipse C++")  
(Sistemas de 64 bits: [Eclipse Helios C/C++](http://www.eclipse.org/downloads/packages/eclipse-ide-cc-developers/heliosr "Eclipse C++"))

E escolha a versão compatível com sua maquina.

Após o download é necessário instalar algum compilador de C e ou C++.  
**Windows:** <http://sourceforge.net/projects/mingw/files/Automated%20MinGW%20Installer/>

**Linux(Ubuntu):** \$sudo apt-get install g++ gcc

 

**Criando um Novo Projeto:**
----------------------------

Após a instalação de um compilador, basta iniciar o seu Eclipse recém baixado, clicar File-\>New-\>C++ Project(ou C Project dependendo do que você quer).  
Escolha um nome para o projeto, Ex: Projeto1.  
Selecione um Toolchain(mingw para windows, linux gcc para ubuntu, ou seu compilador preferido) e clique em "next".  
Depois escolha o que você quer usar, realease(executavel normal) e ou debug(debugger) e clique em "finish".

Pronto! Seu projeto em C/C++ em Eclipse já está pronto para ser usado.

**Adicionando Arquivos Fonte ao Projeto:**
------------------------------------------

Para incluir um arquivo ao projeto, clique com o botao direito no projeto, vá em "new-\>file" e digite o nome do arquivo.

Opcionalmente você pode escolher criar um arquivo Header(arquivo.h), Source(arquivo.c/cpp) ou uma classe(classe.h e classe.cpp).

**Executar um Projeto**:
------------------------

Para executar um projeto basta ir em Run-\>Run(Tecla de atalho Ctrl+F11)  
Detalhe, que ao fazer isso seu projeto será automaticamente recompilado.  
Para recompilar um projeto, basta clicar na seta ao lado do icone de um Martelo, e selecionar a opção que você deseja(Release ou Debug).

**Debugando No Eclipse:**
-------------------------

Clique com o botão direito do mouse no canto esquerdo do arquivo(Onde aparece a numeração das linhas) em cima da linha em que você deseja adicionar um ponto de parada(BreakPoint), e selecione a opção Toggle BreakPoint.

Clique em Run-\>Debug(Tecla de atalho F11).  
Será dado um aviso pedindo para mudar para a perspectiva de Debug(aconselho marcar que sim).  
Na perspectiva de debug utilize F6 para avançar e F5 para entrar em um metodo(apesar de eu nunca me entender bem com esse cara, mesmo no Java).

Numa janela ao lado estão disponíveis as variáveis e seus valores, tao como os BreakPoints do seu projeto(você pode habilitar ou desabilita-los por ali se quiser).

**Facilidades do Eclipse**:
---------------------------

Vou falar apenas da mais famosa e mais utilizada de todas:

**Ctrl+Espaço = Auto-Completar.**

Essa opção permite que você acelere sua codificação em um tempo incalculável(Tá eu talvez eu que seja ruim em calculo).  
Ex:  
Classe instanciaComNomeGrande = new Classe();  
...  
Escreva "inst" e aperte Ctrl+Espaço e veja o Eclipse selecionando a instanciaComNomeGrande da lista de possíveis opções para você.  
Mas vai além, após por um . em instanciaComNomeGrande e usar o auto-completar, ele te dará a lista de opções de métodos e variáveis dessa instancia!

Enfim... são muitas as facilidades que essa IDE proporciona, para aqueles que desejam saber melhor sobre as 3 teclas mais uteis da IDE(Ctrl+1, Ctrl+3, Ctrl+Espaco) pode ver esse [post](http://blog.caelum.com.br/as-tres-principais-teclas-de-atalho-do-eclipse/ "As tres principais teclas de atalho do eclipse") que fala bem delas.
