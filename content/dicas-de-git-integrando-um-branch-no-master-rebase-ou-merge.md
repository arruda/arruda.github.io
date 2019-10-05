Title: Dicas de GIT: Integrando um Branch no Master. Rebase Ou Merge?
Date: 2013-11-20 10:20
Author: arruda
Category: programação, Selecionados
Tags: branch, commits, git, integrando, master, merge, rebase
Slug: dicas-de-git-integrando-um-branch-no-master-rebase-ou-merge
Status: published
Attachments: wp-content/uploads/2013/11/Git-logo.jpg

[![]({static}wp-content/uploads/2013/11/Git-logo.jpg "Git-logo"){.aligncenter .size-full .wp-image-1944 width="273" height="114"}]({static}wp-content/uploads/2013/11/Git-logo.jpg)  
Se você está usando **Rebase** ao invés de **Merge** no **Git**, então fica uma dica importantíssima para quando você vai trabalhar com **Branches**.

Rebase? Que isso?
-----------------

Se você não esta usando rebase, bem, aconselho seriamente a dar uma olhada no meu post que ajuda a ver a diferença entre o Rebase e o Merge: [Dicas de GIT: Rebase vs Merge](http://www.arruda.blog.br/programacao/dicas-de-git-rebase-vs-merge/ "Dicas de GIT: Rebase vs Merge").

\[adsense\]

Momento delicado: Integração de um Branch no Master
---------------------------------------------------

Muitas vezes quando vamos implementar uma funcionalidade nova, criamos um branch novo para isso, e depois que ela está funcional juntamos esse branch de volta ao **master**.

Só que normalmente no meio do desenvolvimento dessa funcionalidade, aparece **algo novo no master** e temos que **colocar isso no branch** que estamos trabalhando.  
E ai? Qual deve ser usado nesse caso? Rebase ou Merge?

### Atualizando o Branch com commits do Master {#atualizando_branch_master}

Bem, nesse caso devemos usar o **REBASE**, seguindo o procedimento abaixo.

``` {lang="shell"}
git checkout nova_funcionalidade
git rebase master
```

Isso vai pegar todos os commits que você fez no seu branch e coloca-los depois das alterações provenientes do master, o que deixa até bem organizado, já que todos os commits referentes a essa funcionalidade ficam juntos um do outro, facilitando depois caso você queira reverter apenas essa funcionalidade.

### Juntando o Branch no Master

Antes de mais nada, devemos garantir que nosso branch com a nova funcionalidade está atualizado com o master, portanto execute os comandos mostrados anteriormente, em [Atualizando o Branch com commits do Master](#atualizando_branch_master).  
Depois disso, o que devemos fazer é um **MERGE**, conforme será explicado a seguir.

``` {lang="shell"}
git checkout master
git merge nova_funcionalidade
```

Com isso garantimos que nosso master ficará igual ao nosso branch da nova funcionalidade (que por sua vez garantimos que ele tinha todos os commits do master fazendo o rebase do master nele).

### Revisão

Só para frisar, o procedimento final de quando vamos juntar um branch no master é:

``` {lang="shell"}
git checkout nova_funcionalidade
git rebase master
git checkout master
git merge nova_funcionalidade
```

Espero que essas dica ajudem vocês, assim como me ajudaram também.

Abraços.
