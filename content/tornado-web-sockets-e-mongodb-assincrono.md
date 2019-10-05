Title: Tornado, Web Sockets e MongoDB Assíncrono
Date: 2013-10-04 10:00
Author: arruda
Category: programação, Python, Selecionados, Web
Tags: assincrono, async, mongo, motor, python, tornado, web sockets
Slug: tornado-web-sockets-e-mongodb-assincrono
Status: published
Attachments: wp-content/uploads/2013/10/tornado.png

[![]({static}wp-content/uploads/2013/10/tornado.png "tornado"){.alignnone .size-full .wp-image-1602 width="286" height="72"}]({static}wp-content/uploads/2013/10/tornado.png)

Esses dias estive testando a framework web [Tornado](http://www.tornadoweb.org/en/stable/ "Tornado web page") (originalmente desenvolvida no FriendFeed do Facebook) conhecida por ter suporte a non-blocking I/O na rede e pelo uso de web sockets e decidi falar um pouco da experiência que tive com ela, bem como algumas curiosidades que descobri.

DB Assíncrono
-------------

Ao investigar mais a fundo, descobri que a framework utiliza por padrão o MySQL como banco de dados.  
Na mesma hora fiquei com aquela pulga atrás da orelha, já que até onde sabia o MySQL não trabalhava assíncrono.  
E foi aí que percebi: Ao ler que a framework tinha non-blocking eu já considerei que tudo poderia ser non-blocking,  
mas na verdade é como eles dizem né: A parte de networking é non-blocking, o acesso a disco é diferente.

Então, volta aquela historia... **é importante ler as coisas direito, né xD**

Facilidade e Simplicidade
-------------------------

A framework é bem simplista, muito bacana ela, procurei no repositório oficial no [github](https://github.com/facebook/tornado "Repositorio Tornado no Github") e descobri la uns [exemplos usando web sockets](https://github.com/facebook/tornado/tree/master/demos/websocket "Exemplos usando web socket no github"), e decidi fazer um eu mesmo.  
Fiquei espantado que em apenas um dia, eu que não sabia nada de Web Sockets, nem de Tornado consegui fazer uma app funcional.  
\[adsense\]

Mas e o BD assíncrono?
----------------------

Bem, descobri que existe o projeto chamado [Motor](http://motor.readthedocs.org/en/stable/ "Pagina do Motor") (de **MO**ngo e **TOR**nado) que é implementa um driver em cima do PyMongo que faz ele funcionar de forma assíncrona. Não cheguei a ver as limitações da ferramenta, mas para o teste que eu fiz de um chat tosquinho ela funcionou de boa.

Chega de blablabla, quero código!
---------------------------------

Bem, pra quem quiser o código é bem simples, criei inclusive um arquivo Vagrant para facilitar (basta usar o comando **vagrant up** na pasta, rodar o servidor e acessar a página localhost:8888 pra ver em funcionamento.  
**OBS:** Quem não conhecer o Vagrant aconselho a dar uma olhada neste [post](http://www.arruda.blog.br/programacao/vagrant-e-puppet-como-manter-seu-ambiente-de-desenvolvimento-sempre-igual/ "Vagrant e Puppet – Como manter seu ambiente de desenvolvimento sempre igual"), facilita muito o espelhamento do ambiente de trabalho =)

Quem não usar Vagrant, basta instalar os requirements (**pip install -r requirements.txt**) e o ter instalado o MongoDB.

Aqui segue o [link para o repositório](https://github.com/arruda/Tornado-WS-Assincrono "Tornado-WS-Assincrono") no github.  
E tomei a liberdade de por uma estrutura no código que me facilitasse:  
Em **urls.py** tem o mapeamento das urls, em **handlers** tem os códigos em Python das visões do sistema. e no arquivo **app.py** tem as configurações básicas da aplicação (inclusive a que diz que é para usar o **Motor** no banco de dados).

### Editado

Segue um link de um vídeo, muito bom sobre esse assunto, que a [Anna Cruz](http://www.arruda.blog.br/programacao/tornado-web-sockets-e-mongodb-assincrono/#comment-863 "Comentario da Anna") postou aqui nos comentários: <http://vimeo.com/38972256>
