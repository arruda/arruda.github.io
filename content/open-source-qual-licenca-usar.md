Title: Open Source: Qual Licença Usar?
Date: 2013-10-10 09:00
Author: arruda
Category: programação, Selecionados
Tags: aberto, codigo, licenca, open, opensource
Slug: open-source-qual-licenca-usar
Status: published
Attachments: wp-content/uploads/2013/10/scroll.png

Isso é uma dúvida que aflige muitos que estão começando nesse maravilhoso mundo do código aberto, não é simples e é de extrema importância.

Arruda, tenho mesmo que usar uma licença?
-----------------------------------------

Claro!  
Nunca faça um projeto em código aberto sem estar respaldado por uma licença, depois alguém aparece pega seu código, é bom evitar essas dores de cabeça, e é bem simples de por uma licença, então por que não né?  
**Então, sempre use alguma licença!**  
\[adsense\]

Qual licença devo usar então?
-----------------------------

Bem, vou dar aqui a minha opnião: **Use a [licença MIT](http://opensource.org/licenses/MIT "Licença MIT").**  
Eu prefiro sempre essa ou a [BSD 2-Clause](http://opensource.org/licenses/BSD-2-Clause "BSD 2-Clause") (segundo alguns comentários engraçados, a principal diferença entre uma a MIT e a BSD, seria por que uma foi feita no Leste e outra no Oeste dos Estados Unidos)

### E a GNU GPL?

Honestamente, se você não sabe o que você ta fazendo, não use [GPL](http://www.gnu.org/licenses/gpl.html "GPL"). Digo isso simplesmente por que ela é uma licença mais complexa de se entender, é beeeeeem longa, e complicada, então a menos que você já tenha lido, e relido e compreendido tudo que ela significa, não use ela.

As vezes ela da medo, parece que em algum ponto você vai ler nela algo do tipo:  
"Se você pensar nesse projeto, obrigatoriamente você, seus filhos, seu cachorro, sua ALMA serão obrigatóriamente GPL. Tarde de mais, ao ler esse texto obrigatoriamente você É GPL"  
É como se eles dissessem:  
"Você tem todo o **direito** de ser **obrigado** a ser **livre**, da maneira **como está escrito aqui** neste texto."

### Por que MIT

A MIT é conhecida por ser extremamente simples e não-restritiva, isso é, permite o uso da seu código fonte, sem criar restrições estranhas e complicadas. Na minha opinião o uso de uma licença não restritiva facilita o uso e assim a disseminação dessa.

Pense bem, se coloque no lugar de quem está fazendo um projeto e decide utilizar uma biblioteca que você tenha criado como base.  
Se você olha pra licença dessa biblioteca e em poucas linhas você consegue entender que pode usar ela como bem entender, você não pensa duas vezes.  
Agora... vamos supor que você vai ver a licença, e da de cara com uma GPL da vida... bem... é intimidador... ou você vai procurar outra biblioteca ou não vai usar nenhuma, ou vai ter que ler toda a licença da GPL até entender ela.

Como faço para usar uma licença?
--------------------------------

-   Coloque um arquivo LICENSE com o conteúdo da licença que você escolheu dentro da pasta base do seu projeto.
-   Lembre-se de colocar os dados corretos na licença, como ano e o autor.
-   Coloque no cabeçalho de cada arquivo de código uma nota sobre o copyright e a licença.

Um site muito bacana caso queira saber mais sobre licenças, se estiver ainda em dúvida de qual utilizar, é o [Choose a License](http://choosealicense.com/ "Choose a License"), ele da uma visão geral sobre quando utilizar as licenças mais famosas que tem por ai.

Bonus: Do What the Fuck You Want to Public License
--------------------------------------------------

Essa licença, conhecida também como WTFPL, é como o nome já diz, bem permissiva, e pra quem tem senso de humor, é bem interessante, eis o texto dela na integra:

                DO WHAT THE FUCK YOU WANT TO PUBLIC LICENSE
                        Version 2, December 2004

     Copyright (C) 2004 Sam Hocevar 

     Everyone is permitted to copy and distribute verbatim or modified
     copies of this license document, and changing it is allowed as long
     as the name is changed.

                DO WHAT THE FUCK YOU WANT TO PUBLIC LICENSE
       TERMS AND CONDITIONS FOR COPYING, DISTRIBUTION AND MODIFICATION

      0. You just DO WHAT THE FUCK YOU WANT TO.

É isso, espero que ajude outros a escolherem suas licenças para seus projetos de código aberto (Não deixe de usar uma licença!)

Abraços.

(**OBS:** Defensores da GPL vão adorar esse post)
