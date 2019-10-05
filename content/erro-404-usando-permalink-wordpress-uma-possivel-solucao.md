Title: Erro 404 Usando Permalink Wordpress - Uma Possível Solução
Date: 2011-10-05 10:30
Author: arruda
Category: Web
Tags: .htaccess, 404, erro, mod_rewrite, permalink, solução, wordpress
Slug: erro-404-usando-permalink-wordpress-uma-possivel-solucao
Status: published

A algum tempo eu estive tentando alterar o Permalink do meu blog, porém sem sucesso.  
Até então eu achava que algum plugin que estava dando conflito, mas depois de MUITO pesquisar, descobri onde era o problema.

Cenário do Problema
-------------------

Vou descrever qual era o problema que eu tive, para vocês saberem se é o caso de vocês ou não.

1.  Começo dizendo que se eu criasse um blog do zero, ele já não funcionava.
2.  O arquivo .htaccess tinha as permissões corretas.
3.  Na configuração do VirtualHost tinha já configurado corretamente a opção de AllowOverride All e FollowSymLinks habilitado.
4.  Mesmo sem nenhum plugin, com o tema padrão dava o erro.
5.  **Erro 404 após a mudança do PermaLinks pra qualquer outro sem ser o default.**

Dica
----

Para saber melhor onde se encontra o seu problema, faça o seguinte, verifique se a mensagem da pagina de 404 é uma mensagem de erro padrão do Apache ou se é uma mensagem bonitinha do seu blog dizendo que deu 404.  
Se a pagina de 404 **NÃO é do Wordpress**, então você sabe que é algum erro na configuração do apache!

O Problema
----------

Não meus caros, o problema não estava ai nos tópicos citados, o problema era o seguinte:  
No arquivo .htaccess tinha algo parecido com isso:

``` {lang="xml"}
# BEGIN WordPress

RewriteEngine On
RewriteBase /
RewriteCond %{REQUEST_FILENAME} !-f
RewriteCond %{REQUEST_FILENAME} !-d
RewriteRule . /index.php [L]

# END WordPress
```

Reparem que quando ele faz **IfModule mod\_rewrite.c** ele vai verificar se está habilitado o modulo: mod\_rewrite.c. Se não estiver habilitado, basicamente ele não vai aplicar as mudanças que deveriam ser feitas.

Mas por que raios o mod\_rewrite.c não estaria habilitado?  
Por que aparentemente quando se instala o apache e o php separados no Ubuntu, esse modulo vem **desativado por default.**

Resolvendo o Problema
---------------------

Para ativar o modulo **"mod\_rewrite.c"** use o comando:

``` {lang="bash"}
$ a2enmod rewrite
```

E pronto, basta agora alterar o PermaLink que ele vai funcionar.  
Se com isso ele não funcionar, eu aconselho a verificar os tópicos citados anteriormente, quem sabe um deles não está sendo o seu problema?

### Se ainda assim não funcionar...

Se depois de habilitar o mod\_rewrite.c, ainda assim você não estiver conseguindo fazer isso funcionar, talvez isso resolva:  
Verifique se na configuração do seu VirtualHost no apache, se você tem a seguinte configuração:

``` {lang="shell"}
       
        Options Indexes FollowSymLinks MultiViews
        AllowOverride All
        Order allow,deny
        allow from all
    
```

Atenção especial para a linha **AllowOverride All**.  
Depois de muito tempo descobri que isso também era necessário para fazer funcionar(dependendo do tipo de instalação que você faça do PHP e do Apache).  
Não esqueça de reiniciar o Apache, e pronto.

Espero que tenha ajudado.  
Abraços.
