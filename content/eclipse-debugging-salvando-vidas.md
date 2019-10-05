Title: Eclipse Debugging - Salvando Vidas
Date: 2012-03-24 17:58
Author: arruda
Category: C/C++, Django, Java, programação, Python, Selecionados
Tags: C, CPP, debug, debugging, Django, Eclipse, Java, pydev
Slug: eclipse-debugging-salvando-vidas
Status: published
Attachments: wp-content/uploads/2012/03/debug_wiz_white.png, wp-content/uploads/2012/03/debug.jpg, wp-content/uploads/2012/03/download.jpg, wp-content/uploads/2012/03/breakpoint.png

Mais uma vez vou falar dessa ferramenta(dessa vez bem rápido, só para relatar o ocorrido recente).  
Estava ajudando minha namorada com um exercício de C no PC.  
Até que depois de um bom tempo tentando entender por que raios o **printf** não printava(nada como um **fflush(stdout)** para resolver) é que eu falei para ela usar o debug, e espantada eu fui explicar como funcionava.

A ideia para quem não sabe é simples:

1.  você marca a linha em que você quer que o programa pare(**BreakPoint**):  
   [![break point]({static}wp-content/uploads/2012/03/breakpoint.png "breakpoint"){.alignnone .size-full .wp-image-1058 width="428" height="409"}]({static}wp-content/uploads/2012/03/breakpoint.png)
2.  Depois clique no botão de debbug: [![]({static}wp-content/uploads/2012/03/debug.jpg "debug"){.alignnone .size-full .wp-image-1062 width="38" height="27"}]({static}wp-content/uploads/2012/03/debug.jpg)
3.  Usando as teclas **F6** para ir passo-a-passo, e **F8** para seguir direto para o próximo breakpoint é possível navegar pelo seu código observando exatamente o que está acontecendo.

C/C++
-----

É claro que os passos são o modo genérico(Java), assim para funcionar isso em C é preciso dar build([![build]({static}wp-content/uploads/2012/03/download.jpg "build"){.alignnone .size-full .wp-image-1064 width="37" height="19"}]({static}wp-content/uploads/2012/03/download.jpg)) no Debug antes de debugar.

Django
------

É claro que depois disso eu me perguntei:  
*"Pera ai... Porque raios não uso isso nos meu projetos em Django?"*

Depois de 2 minutos configurando algumas coisas(minha estrutura de diretório de projetos não é a padrão, então tive que adicionar outras pastas no PYTHON\_PATH do projeto).  
Depois disso é o mesmo procedimento: Colocar um breakpoint e executar o servidor com o Debug.

Foi uma experiencia bacana, fui indo passo a passo por todo o processo do django desde o momento em que ele terminou uma view minha até o momento em que ele entrega a resposta... passando pelos middlewares e etc =)
