Title: Unreal Engine Mobile
Date: 2011-04-26 15:00
Author: arruda
Category: Jogos, UDK
Tags: mobile, udk, ue3, unreal engine
Slug: unreal-engine-mobile
Status: published

Mais uma vez venho lhes falar da Unreal Engine, desta vez algo que era desconhecido para mim até pouco tempo: UE para desenvolvimento mobile.

Já havia dado uma rápida introdução ao que as ferramentas do Unreal Ed possibilitam, então decidi olhar a fundo as vantagens e as limitações das mesmas.

Fiquei muito contente com o que vi, não só com os jogos resultantes, mas também com o incentivo para a área. Eles da EpicGames não são bobos, sabem que app Mobile são a onda hoje em dia, e não deixaram por menos com a Engine.

Compatibilidade
---------------

Atualmente a UE3 tem maior compatibilidade com sistemas IOs, Ipad, Iphone 3GS e similares.  
No caso para Android ainda não é algo muito certo, tirando alguns modelos específicos como o Samsumg Galaxy Tab.  
Ela também roda no novo console feito pela Sony, o NGP, sem problemas.

UE3 Mobile vs UE3
-----------------

A verdade é que se você está desenvolvendo uma aplicação usando UE3, é quer q ela seja multiplataforma(PC e Mobile), então eis alguns detalhes:

-   Materials: Para a plataforma Mobile, a forma como os Materials são feitos e processados é um pouco diferente. Veja essa referencia: [Materials](http://udn.epicgames.com/Three/MobileMaterialReference.html "Materials for Mobile")
-   A maioria das coisas serão convertidas para que sejam suportadas por um mobile, ao gerar tal versão. Entretanto vale lembrar que pontos como usabilidade de memoria, limitar a quantidade de coisas nos Levels é uma boa forma de reduzir isso.
-   Outra possível solução é criar 2 tipos diferentes de jogos, mas com scripts e funcionalidades similares, dessa forma você pode ter num jogo de PC um mapa gigante cheio de itens e etc, e no Mobile salas pequenas com menos detalhes.

Ativando a UE3 para Mobile
--------------------------

Para fazer que sua Unreal Engine trabalhe para Mobile, é preciso alterar alguns arquivos de configuração da mesma (ao que parece é possível baixar uma versão já totalmente configurada para mobile, mas ainda não achei isso).

A maioria das configurações podem ser encontradas no arquivo: "Engine/Config/BaseEngine.ini". Essas configurações também podem ser sobrescritas por seu "DefaultEngine.ini" dentro do seu diretório "GameName/Config". Mais informações sobre [Mobile Settings](http://udn.epicgames.com/Three/MobileSystemSettings.html "Mobile Settings").

Domínio do Mercado
------------------

Ao que tudo indica, e pelo que muitos estão dizendo, a UE3, agora que chegou ao mercado Mobile, veio para ficar. Provavelmente os melhores gráficos que você vera num Mobile nos dias que viram serão provenientes da UE3. Então vale a pena conferir e aproveitar a onda.  
Para você ter uma noção, o jogo Infinity Blade feito pela EpicGames, era pra ser um jogo simples que apenas mostra o poder da engine em mobiles. Entretanto, depois de pouco tempo de venda, até mesmo o pessoal da EpicGames ficou espantado com a quantidade de pessoas comprando o jogo.

Também, não é para menos, confira por si próprio se não da vontade de jogar isso no teu IOs:  
<iframe title="YouTube video player" width="640" height="390" src="http://www.youtube.com/embed/JDvPIhCd8N4" frameborder="0" allowfullscreen></iframe>

E ai, pode falar, já ta baixando o jogo né? =)

Referencia
----------

[UDN Mobile Home](http://udn.epicgames.com/Three/MobileHome.html "Mobile Home")

[UDK Mobile](http://www.udk.com/mobile "UDK Mobile")

 
