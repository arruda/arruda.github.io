Title: Duplicando VM no VirtualBox
Date: 2011-07-13 16:32
Author: arruda
Category: Aleatoriedades
Tags: clonar, clone, clonevdi, duplicate, vboxmanager, virtualbox, VM
Slug: duplicando-vm-no-virtualbox
Status: published
Attachments: wp-content/uploads/2011/07/vm_1.png, wp-content/uploads/2011/07/vm_2.png

Infelizmente o VirtualBox não possui uma opção para fazer isso(pelo menos não diretamente). Porém após um pouco de pesquisa, descobri uma maneira para duplicar sua VM no VirtualBox:

Vá até a pasta onde está salvo o vdi(virtual driver image, vulgo disco da sua maquina).

Dentro da pasta execute:  
**(Linux):** VBoxManager clonevdi **caminho/completo/original.vdi** **caminho/completo/clone.vdi**

Depois basta mandar criar uma VM nova, e quando tiver que escolher o disco, selecione a opção de escolher um disco já existente.  
[![]({static}wp-content/uploads/2011/07/vm_1.png "vm_1"){.aligncenter .size-full .wp-image-492 width="571" height="392"}]({static}wp-content/uploads/2011/07/vm_1.png)  
Na próxima tela adicione o clone.vdi e selecione ela.  
[![]({static}wp-content/uploads/2011/07/vm_2.png "vm_2"){.aligncenter .size-full .wp-image-493 width="636" height="498"}]({static}wp-content/uploads/2011/07/vm_2.png)

Pronto, sua nova VM é um clone da anterior.
