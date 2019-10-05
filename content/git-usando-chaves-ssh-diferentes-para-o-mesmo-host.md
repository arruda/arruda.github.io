Title: GIT - Usando Chaves SSH Diferentes Para o Mesmo Host
Date: 2013-11-02 18:43
Author: arruda
Category: programação, Selecionados
Tags: chave, config, diferente, github, heroku, host, rsa, ssh
Slug: git-usando-chaves-ssh-diferentes-para-o-mesmo-host
Status: published
Attachments: wp-content/uploads/2013/11/ssh-logo.jpg

Uma dica para quem usa SSH para fazer push em reposítórios GIT, mas gostaria de usar uma chave SSH diferente para diferentes repositórios, mas que sejam do mesmo host:

Caso de Uso
-----------

Bem, posse ser meio estranho, mas vou dar um exemplo de como você pode querer aproveitar isso:

Vamos supor que você trabalha na empresa **Empresa SA** mas também tem diversos projetos pessoais.  
Para sua empresa, você deve usar uma chave SSH específica, e claro, para seus projetos pessoas você usa outra chave SSH.  
Considere que ambos os repositórios estão no Github (mesmo Host).  
Assim você tem um projeto pessoal em **git\@github.com:arruda/um\_proj.git** e está trabalhando em um da sua empresa que está em **git\@github.com:empresa\_sa/outro\_proj.git**.

Pronto, temos o cenário, como fazemos para o SO entender que no repositório do projeto pessoal você quer usar sua chave SSH pessoal, e que no do trabalho você quer utilizar sua chave SSH do trabalho?  
\[adsense\]

Solução
-------

Para isso devemos fazer as coisas em 2 etapas bem simples:

### Host com Apelido

Vamos começar definindo "apelidos" para um dos repositórios, assim será possível diferenciar os host de cada um dos repositórios.

Para isso edite o arquivo de configuração de SSH do seu usuário, em sistema Debian ele costuma ficar em:  
**\~/.ssh/config**  
Ponha no fim desse arquivo, o seguinte texto:

``` {lang="shell"}
Host repo_da_minha_empresa_sa
  HostName github.com
  IdentityFile ~/.ssh/minha_chave_da_empresa
  User git
```

Onde:

-   **repo\_da\_minha\_empresa\_sa**: Um apelido intuitivo para esse host
-   **github.com**: Hostname de onde está hospedado o remote do GIT
-   **\~/.ssh/minha\_chave\_da\_empresa**:Caminho para a chave SSH que você usa no seu trabalho
-   **git**:Usuário que é usado no SSH (é o que vem antes do "**@**" em git\@github.com:empresa\_sa/outro\_proj.git)

Com isso definimos que onde houver o Host: "**repo\_da\_minha\_empresa\_sa**", será usado a chave SSH do seu trabalho ao invés da padrão.

Com isso terminamos o primeiro passo.

### Colocando o Apelido no reposítorio Git

Agora devemos ir para o repositório local do seu projeto do trabalho, e nele editar as configurações do mesmo.  
Para isso, dentro do repositório abra o seguinte arquivo: **.git/config**  
Procure por: **\[remote "origin"\]**, essa seção deve ser parecida com a seguinte:

``` {lang="shell"}
[remote "origin"]
    fetch = +refs/heads/*:refs/remotes/origin/*
    url = git@github.com:empresa_sa/outro_proj.git
```

O que você vai alterar é que no lugar de "github.com", você vai colocar o apelido que você definiu no arquivo **\~/.ssh/config**, neste exemplo ficaria:

``` {lang="shell"}
[remote "origin"]
    fetch = +refs/heads/*:refs/remotes/origin/*
    url = git@repo_da_minha_empresa_sa:empresa_sa/outro_proj.git
```

Pronto, agora quando for utilizar o SSH nesse repositório, para fazer pull, push e etc, ele irá utilizar a chave SSH do seu trabalho, ao inves da padrão. E seu repositório pessoal continuará utilizando a chave padrão (usando chave RSA é a chave **id\_rsa**).

Com isso concluo essa importante dica (**muito importante também se você tem um heroku pessoal e um heroku da sua empresa**).

Para uma boa referência, segue um dos links que me ajudaram nessa questão:  
[Specify an SSH key for git push without using \~/.ssh/config](http://stackoverflow.com/questions/7927750/specify-an-ssh-key-for-git-push-without-using-ssh-config "Specify an SSH key for git push without using ~/.ssh/config")

Abraços.
