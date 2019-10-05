Title: Steam no Linux - Primeira Impressão
Date: 2015-03-31 21:58
Author: arruda
Category: Jogos
Tags: download, jogar, jogo, libGL.so.1, linux, nvidia, placa dedicada, steam
Slug: steam-no-linux-primeira-impressao
Status: published
Attachments: wp-content/uploads/2015/03/Mac_OS_X_Steam_Icon_by_ssj4saturnduo.png

Essa semana decidi testar o **Steam** no **linux**, e ver quais jogos eu podia **jogar** nele, eis minha experiência:

\[adsense\]

Instalação
----------

Meu SO é um **Ubuntu 14.04** usando o **Gnome 3**, por isso achei que fosse ter infindáveis problemas, mas no fim das contas, para instalar só foi preciso ir no site da [Steam](http://store.steampowered.com/about/ "Site de download do steam") e clicar em download.

Uma vez feito o **download** do **.deb** executei ele e concluí assim a instalação.

Epa, não ta Rodando
-------------------

Agora para rodar, ai foi outra história.

Quando ia abrir o **Steam** recebia o aviso: **"Missing 32-bit libraries: libGL.so.1"**.

Para resolver esse problema não foi assim tão dificil quanto imaginei, consegui achar essa referência: [Fix for Steam: "Missing 32-bit libraries: libGL.so.1"](http://ubuntuforums.org/showthread.php?t=2233005 "Fix for Steam: "Missing 32-bit libraries: libGL.so.1"").

Basicamente a ideia é criar/editar o arquivo **/etc/ld.so.conf.d/steam.conf**, colocando nele:

``` {lang="shell"}
/usr/lib32
/usr/lib/i386-linux-gnu/mesa
```

e depois rodar:

``` {lang="shell"}
$ sudo ldconfig
```

**Não** precisei re-instalar o *libgl1-mesa-glx:i386*, foi só tentar abrir novamente o Steam que deu tudo certo.

Jogando com a Placa de Video Dedicada
-------------------------------------

No meu caso tenho uma Nvidia, e já tinha instalado os drives da placa de video (acho que é o Bumblebee), assim para rodar alguma coisa usando essa placa era só rodar usando o comando **primusrun**.

Então, seguindo a pagina da própria Steam, para fazer um determinado jogo rodar com esse comando, basta que, na Steam:

-   Selecione o Jogo
-   Clique em **Proprieties**
-   Clique **"Set Launch Options..."**
-   e coloque: **primusrun %command%**
-   clicar em **OK** e **Close**

Depois disso o jogo vai rodar usando a placa Nvidia =D

Jogos disponíveis
-----------------

Não tenho uma infinidade de jogos, então não sei se vale muito o que vou dizer, mas dos meus **13 jogos** (nossa! tudo isso!) **8 rodam no linux**.

Alguns dos jogos que rodam no linux:

-   BioShock Infinite
-   The Cave
-   Dota 2
-   Portal 2

Geral
-----

Bem, no geral achei que o desempenho do Steam e dos jogos foi muito bom, não senti nenhum problema (até agora...).

Então, para quem ta deixando para depois, aconselho a dar uma chance a jogar seus jogos no linux também... quem sabe um dia não de pra **aposentar de vez o windows**?
