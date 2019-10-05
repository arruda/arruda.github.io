Title: Tutorial UDK: Primeira Parte
Date: 2011-05-11 12:00
Author: arruda
Category: Jogos, Selecionados, UDK
Tags: basico, mapa, tutorial, udk, ue3, unreal engine
Slug: tutorial-udk-primeira-parte
Status: published
Attachments: wp-content/uploads/2011/05/4.png, wp-content/uploads/2011/05/12.png, wp-content/uploads/2011/05/6.png, wp-content/uploads/2011/05/3.png, wp-content/uploads/2011/05/1.png, wp-content/uploads/2011/05/5.png, wp-content/uploads/2011/05/2.png, wp-content/uploads/2011/05/11.png, wp-content/uploads/2011/05/13.png, wp-content/uploads/2011/05/61.png, wp-content/uploads/2011/05/7.png, wp-content/uploads/2011/05/9.png, wp-content/uploads/2011/05/8.png, wp-content/uploads/2011/05/10.png

Tutorial UDK
============

Tutorial 1: Criando um mapa de teste
------------------------------------

Bem, antes de mais nada é preciso baixar o UDK(de preferência a mesma versão que estamos usando no tutorial: **UDK-2011-04**) do [site da UDK](http://download.udk.com/UDKInstall-2011-04-BETA.exe "UDK").  
Após instalar o programa, navegue para a pasta do mesmo(ex: c:/UDK/UDK-2011-04), é nessa pasta que acontecerá toda a mágica.

A ideia geral do tutorial é fazer um simples jogo de um mapa só em que o personagem principal tem uma visão no estilo dos antigos jogos arcade(lateral).  
Existem diferentes formas de se abordar a criação de jogos na UDK, muitas são feitas simplesmente pelo próprio UnrealEditor, que permite uma forma simples de alterar diversas funcionalidades com apenas cliques do mouse. E tem também o UnrealScript, que permitem também fazer praticamente tudo que você possa imaginar, mas em forma de códigos.

Apesar de eu preferir usar códigos para tudo, tenho que admitir que é tão simples usar o UnrealEditor, que tenho que começar por ele.  
Então vamos começar!

UnrealEditor
------------

Para começarmos basta executar o programa UDK Editor:  
[![]({static}wp-content/uploads/2011/05/1.png "UDK"){.aligncenter .size-full .wp-image-309 width="734" height="252"}]({static}wp-content/uploads/2011/05/1.png)

Após executar o editor , vamos criar um mapa simples(bem simples) e fazer dele um mapa de teste para nosso futuro jogo.

Para isso clique com o botão direito do mouse sobre o cubo de “Brushes”:

[![]({static}wp-content/uploads/2011/05/2.png "Cube Brush"){.size-full .wp-image-310 .aligncenter width="74" height="204"}]({static}wp-content/uploads/2011/05/2.png)  
Na pequena tela que vai abrir vamos setar as configurações do chão, ou uma plataforma, do nosso mapa, que iremos criar agora. Coloque as seguintes informações:

[![]({static}wp-content/uploads/2011/05/3.png "Brush Properties"){.aligncenter .size-full .wp-image-312 width="349" height="330"}]({static}wp-content/uploads/2011/05/3.png)E clique em Build.

\[adsense\]

Agora temos uma moldura da plataforma, entretanto, ainda falta mais um passo antes de construirmos ela de verdade.  
Abra o “Content Browser”(Ctrl+Shift+f) ou clique no icone:  
[![]({static}wp-content/uploads/2011/05/4.png "Content Browser"){.aligncenter .size-full .wp-image-313 width="210" height="27"}]({static}wp-content/uploads/2011/05/4.png)Essa tela que se abriu se mostrará ainda muito útil, porém vamos direto ao que nos interessa, vamos dar uma textura, um material para nossa plataforma. Para isso clique no package “UDKGame” da lista de Packages. E no filtro marque “Materials”, e procure pelo nome: “M\_LT\_Base\_03”.  
Isso lhe mostrará o material que vamos usar como base para nossa plataforma(se quiser você pode por outro, mas só para agilizar estou usando esse mesmo).  
[![]({static}wp-content/uploads/2011/05/5.png "Content Browser 2"){.aligncenter .size-full .wp-image-314 width="814" height="555"}]({static}wp-content/uploads/2011/05/5.png)Selecione o material e feche o Content Browser.

Agora que nosso material já está selecionado, vamos criar de uma vez por todas a plataforma:  
Clique no botao CSG Add:  
[![]({static}wp-content/uploads/2011/05/61.png "CSG Add"){.aligncenter .size-full .wp-image-316 width="129" height="101"}]({static}wp-content/uploads/2011/05/61.png)  
E pronto, sua plataforma está feita.

Agora vamos fazer com que possa ser possível jogar esse mapa.  
Para isso clique com o botão direito na plataforma, vá em Add Actor-\>Add PlayerStart:  
[![]({static}wp-content/uploads/2011/05/6.png "Add PlayerStart"){.aligncenter .size-full .wp-image-315 width="603" height="446"}]({static}wp-content/uploads/2011/05/6.png)  
Agora vamos por uma iluminação básica no nosso mapa:  
Para isso clique com o botão direito na plataforma, vá em Add Actor-\>Add Light(Point):

Depois clique e arraste na seta que aponta para cima na lampada que foi criada, para subir a luz no mapa:  
[![]({static}wp-content/uploads/2011/05/7.png "Up Light"){.aligncenter .size-full .wp-image-318 width="573" height="583"}]({static}wp-content/uploads/2011/05/7.png)  
Lembre-se de salvar o mapa. Vamos salvá-lo como “TUT-mapa1.udk”:  
[![]({static}wp-content/uploads/2011/05/8.png "Save"){.aligncenter .size-full .wp-image-319 width="564" height="420"}]({static}wp-content/uploads/2011/05/8.png)  
Agora, para finalizar vamos dar “Build” na nossa geometria e nas luzes do mapa(apesar de serem poucas coisas para computar, é importante fazer isso).  
Clique em “Build Geometry”, e espere terminar(provavelmente dará uns erros, mas não tem problema, apenas clique em Ok).  
[![]({static}wp-content/uploads/2011/05/9.png "Build Geometry"){.aligncenter .size-full .wp-image-320 width="174" height="48"}]({static}wp-content/uploads/2011/05/9.png)  
Para a luz, clique em “Build Lighting”  
[![]({static}wp-content/uploads/2011/05/10.png "Build Lighting"){.aligncenter .size-full .wp-image-321 width="174" height="51"}]({static}wp-content/uploads/2011/05/10.png)Isso irá abrir uma janela com informações do que você quer utilizar nesse build. Apenas clique em Ok, deixe tudo como está.  
[![]({static}wp-content/uploads/2011/05/11.png "Build Lightning 2"){.aligncenter .size-full .wp-image-322 width="280" height="382"}]({static}wp-content/uploads/2011/05/11.png)Espere um tempo, depois que o SwarmAgent rodar, você verá uma janela provavelmente com erros, mas tudo bem, clique em Ok.

Salve o mapa.

Agora nosso mapa de teste está pronto para ser executado. Você pode testa-lo de dentro do próprio UnrealEditor, usando o PIE(Play In Editor):  
[![]({static}wp-content/uploads/2011/05/12.png "PIE"){.aligncenter .size-full .wp-image-323 width="130" height="38"}]({static}wp-content/uploads/2011/05/12.png)Ou aperte F8.  
Pronto! Você já pode andar pelo seu grande e vasto mapa de teste:  
[![]({static}wp-content/uploads/2011/05/13.png "PIE2"){.aligncenter .size-full .wp-image-324 width="1031" height="801"}]({static}wp-content/uploads/2011/05/13.png)

Com isso concluo a primeira parte do tutorial, com um mapa de testes. Se quiser ampliar seu conhecimento na área de edição de mapas aconselho ver essa lista de vídeos do 3Dbuzz:  
<http://www.3dbuzz.com/vbforum/sv_showvideo.php?v=3743> (É preciso registrar para assistir, mas não tem problema, pois é de graça).

Fique ligado para a parte 2 do tutorial, onde irei mostrar como criar um pacote para compilar seu próprio projeto.

Abraços.
