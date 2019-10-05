Title: Incluindo Programas no Gnome-Do
Date: 2012-02-01 09:12
Author: arruda
Category: Aleatoriedades, Selecionados
Tags: add, aplicativo, application, do, gnome, menu, ubuntu. gnome-do
Slug: incluindo-programas-no-gnome-do
Status: published
Attachments: wp-content/uploads/2012/02/gnome.png

<p>

Depois de um tempo achei uma maneira simples de adcionar um programa no gnome-do(Talvez não a maneira mais eficiente e sem bugs, mas ainda assim funciona):  
Primeiro é uma boa criar a pasta \~/bin para manter todos seus executaveis(ou Links)  

<script src="https://gist.github.com/1716674.js?file=primeiro.sh"></script>

  
Depois altere seu \~/.bashrc para que o mesmo inclua o novo diretorio na sua PATH:  

<script src="https://gist.github.com/1716674.js?file=add_bashrc.sh"></script>
</p>
<p>

Vou incluir o eclipse como exemplo:  

<script src="https://gist.github.com/1716674.js?file=segundo.sh"></script>
</p>
<p>

Agora faça:  

<script src="https://gist.github.com/1716674.js?file=terceiro.sh"></script>
</p>
<p>

Coloque o seguinte conteudo:  

<script src="https://gist.github.com/1716674.js?file=quarto.sh"></script>
</p>

Salve(talvez seja preciso deslogar e logar) e você agora já verá a mesma no menu de aplicacoes do ubuntu, dentro de desenvolvimento.

Reinicie o Gnome-Do e agora ao escrever Eclipse ele ira mostrar e abrir o que foi configurado.  
=D
