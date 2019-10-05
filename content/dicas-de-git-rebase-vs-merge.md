Title: Dicas de GIT: Rebase vs Merge
Date: 2013-09-26 10:30
Author: arruda
Category: programação, Selecionados
Tags: git, merge, pull, rebase, vs
Slug: dicas-de-git-rebase-vs-merge
Status: published
Attachments: wp-content/uploads/2013/09/exg2.png, wp-content/uploads/2013/09/exg1.png, wp-content/uploads/2013/09/exg3.png, wp-content/uploads/2013/09/exg4.png

Graças as dicas dos meus antigos colegas de trabalho la na Globo.com (Lucas, Hélio e Gustavo) que fiquei sabendo dessa dica importantes do Git.

Diferença entre Rebase e Merge
------------------------------

Considerando que haja a princípio 3 commits, **A, B e C**:  
[![]({static}wp-content/uploads/2013/09/exg1.png "3 commits originais"){.alignnone .size-full .wp-image-1533 width="255" height="68"}]({static}wp-content/uploads/2013/09/exg1.png)

Em seguida o desenvolvedor José criar o commit **D** e o desenvolvedor Manuel o commit **E**:  
[![](http://www.arruda.blog.br/wp-content/uploads/2013/09/exg2-300x97.png "Dois devs fazem commits"){.alignnone .size-medium .wp-image-1535 width="300" height="97"}]({static}wp-content/uploads/2013/09/exg2.png)

\[adsense\]

### Merge

[![](http://www.arruda.blog.br/wp-content/uploads/2013/09/exg3-300x97.png "Fazendo merge"){.alignnone .size-medium .wp-image-1538 width="300" height="97"}]({static}wp-content/uploads/2013/09/exg3.png)  
Como podemos observar, ao utilizar o Merge um novo commit **M** é criado, e ambos os commits **D** e **E** continuam no mesmo lugar. Isso acaba criando uma forma de *diamante* que confunde bastante quando vamos olhar os commits (além de criar um commit a mais).

### Rebase

[![](http://www.arruda.blog.br/wp-content/uploads/2013/09/exg4-300x97.png "Usando rebase"){.alignnone .size-medium .wp-image-1540 width="300" height="97"}]({static}wp-content/uploads/2013/09/exg4.png)

Ao utilizar o Rebase, um novo commit **R** com conteúdo identido ao do commit **M** anterior é criado, mas eliminamos o commit **E**. Com isso o histórico fica mais linear e fácil de ler e com um commit a menos.

**Atenção:** Como foi dito anteriormente, o Rebase altera a arvore de commits, assim se for feito um push dessa alteração, as arvores dos outros desenvolvedores vão também ser reescritas e isso pode gerar uma baita confusão! Portanto não é uma boa ideia fazer pushar o Rebase, a menos que queira apanhar do seu time!

Quando usar Rebase então?
-------------------------

Uma dica fantástica é utilizar o Rebase quando fizer o Pull de algum remote, Ex:

``` {lang="shell"}
$ git pull --rebase origin master
```

Com isso todos os seus commits são 'arrancados' da arvore, os commits do remote são colocados, e no final são 'recolocados' seus commits... assim independente de você ter commits na frente do remote, fazendo um pull vai colocar todos seus commits sempre juntos no topo (facilitando também para reverter alguma funcionalidade sem impactar em outras alterações que poderiam ter ficado commitadas no meio).

E fica ainda melhor, você pode configurar nas configurações globais (ou apenas locais) que sempre que utilizar o rebase em um determinado Branch:

``` {lang="shell"}
$ git config --global branch.nome_do_branch.rebase true
```

No caso do Branch master:

``` {lang="shell"}
$ git config --global branch.master.rebase true
```

Para fazer isso localmente em um único repositório no lugar de global, basta retirar o **'--global'**.

Exemplo Prático
---------------

Aproveitando a [dúvida do Norton](http://www.arruda.blog.br/programacao/dicas-de-git-rebase-vs-merge/#comment-910), vou colocar aqui no post o que passei pra ele no comentário:  
Criei um repositório no github que ilustra esses dois casos, quando tem o merge e quando tem o rebase:  
[Exemplo da Forma de Diamante no Git](https://github.com/arruda/exemplo_diamante_git/network "Exemplo da Forma de Diamante no GIt")

O **segundo** e o **terceiro** commit estão usando **merge**, e os **dois ultimos** usando **rebase**, você pode ver como fica mais claro a visualização usando rebase do que usando merge, que cria essas ramificações e depois volta para a linha principal dos commits.

Por hoje é só!

Referência
----------

As imagens e o exemplo da diferença entre o Merge e o Rebase foram retiradas da desta resposta no [StackOverflow](http://stackoverflow.com/a/16666418/680611 "Referencia do Merge vs Rebase")
