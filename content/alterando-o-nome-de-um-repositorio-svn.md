Title: Alterando o Nome de Um Repositorio SVN
Date: 2011-08-18 11:48
Author: arruda
Category: Aleatoriedades
Tags: alterar, nome, repositorio, svn, trac
Slug: alterando-o-nome-de-um-repositorio-svn
Status: published

Caso você tenha criado um repositório, para um projeto, mas no meio do caminho o mesmo mudou de nome. Ou se por alguma razão o antigo nome do repositório não lhe serve mais. A solução para isso se baseia em dois comandos do **svnadmin**: *dump* e *load*.

Alterando o SVN
---------------

Para fazer isso, primeiro vá para o local onde está o repositório, e usar o dump:

``` {lang="bash"}
$cd /path/do/repositorio
$svnadmin dump nomeAntigoRepos > nomeAntigoRepos.dump
```

Isso fará com que seja criado um arquivo "nomeAntigoRepos.dump" com as informações dos seus commits e etc.  
**OBS:** Esse arquivo .dump pode ficar bem grande, dependendo de qual for o porte do seu SVN.

Em seguida, crie um novo repositório com o nome desejado, e faça **load** do seu arquivo *.dump* nele:

``` {lang="bash"}
$svnadmin create nomeNovoRepos
$svnadmin load nomeNovoRepos < nomeAntigoRepos.dump
```

Agora já pode excluir o nomeAntigoRepos.dump e o antigo repositório também.

Alterando o Trac
----------------

Caso esteja usando o Trac, e se quiser alterar o nome do Trac também, deve ser feito:

``` {lang="bash"}
$trac-admin /path/do/trac hotcopy /path/do/novoTrac
```

Depois disso abra o conf(**trac.ini**) desse novoTrac, e edite a linha:  
**"repository\_dir ="** para o novo repositório SVN criado.  
Por fim, execute:

``` {lang="bash"}
$trac-admin . resync
```

**OBS:**Esse comando deve ser usado de dentro do diretório do novoTrac.
