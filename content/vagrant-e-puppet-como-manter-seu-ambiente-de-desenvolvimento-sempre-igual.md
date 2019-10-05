Title: Vagrant e Puppet - Como manter seu ambiente de desenvolvimento sempre igual
Date: 2013-09-12 15:18
Author: arruda
Category: Ambiente de Trabalho, programação, Selecionados
Tags: ambiente de trabalho, igual, puppet, vagrant
Slug: vagrant-e-puppet-como-manter-seu-ambiente-de-desenvolvimento-sempre-igual
Status: published

Bom dia a todos!  
Voltando agora a ativa no meu blog, decidi escrever sobre algo que andei estudando(conforme já havia mencionado em um [post anterior](http://www.arruda.blog.br/aleatoriedades/voltando-aos-estudos-de-verdade/ "Voltando aos estudos… de verdade…")) sobre uma forma mais fácil de desenvolver projetos em equipe.

Problemas Comuns
----------------

Quem já fez algum sistema web com mais de uma pessoa já viu que sempre acontece de você instalar e configurar todo o ambiente na sua máquina e tudo ta indo as mil maravilhas, mas quando seu colega vai instalar na máquina dele... de repente começam a aparecer erros e mais erros loucos, e depois de 1 semana de luta você finalmente consegue ganhar essa batalha. Mas, 2 dias depois, outra pessoa entra na equipe e lá vai você novamente, até o ponto em que você já está compilando manualmente algumas bibliotecas é que você pensa como seria bom se todos tivessem a mesma máquina.

Ou então, depois de um bom tempo, quando todos as máquinas ficaram prontas, e o desenvolvimento está correndo solto, ninguém pode parar vocês... até que na hora do deploy pra produção vocês percebem que as consultas ao banco não estão fazendo o menor sentido... depois de investigar um pouco, descobre-se que em produção vocês estão usando um banco de dados na versão X e em desenvolvimento estão usando na versão X+1. E novamente vocês pensam : "Seria tão bom se em produção também fosse o mesmo ambiente que eu uso em desenvolvimento".

Solução
-------

Conheçam o [Vagrant](http://www.vagrantup.com/ "Vagrant")!  
Essa ferramente permite replicar um ambiente de trabalho facilmente entre os desenvolvedores e o ambiente de produção.  
Basicamente ele cria para você uma maquina virtual com a partir de um arquivo texto que possuí diversas configurações da máquina, como o sistema operacional dela, quantidade de memória, nome, endereço ip e etc...

E para ter sua máquina pronta para o uso é bem simples, uma vez instalado o Vagrant, basta que, dentro diretório em que está o arquivo de configuração do vagrant, rode o comando:

``` {lang="shell"}
$ vagrant up
```

Pronto! Ele vai montar tudo sozinho pra você e em pouco tempo você tem a máquina que está descrita no arquivo de configuração.

Agora se você quiser que seu colega tenha o mesmo ambiente que você, basta ele pegar o mesmo arquivo de configuração que você e rodar o comando *"vagrant up"*!

Como o Vagrant funciona a princípio em cima do [VirtualBox](https://www.virtualbox.org/ "VirtualBox") (Maquina Virtual da Oracle, que é de graça), é possível ter a mesma máquina independente do sistema operacional que você estiver usando na sua maquina, Linux, Mac ou Windows (esse tem suas ressalvas, pra variar)!

Instalando Programas e Configurando Sua Máquina
-----------------------------------------------

O arquivo de configuração do Vagrant permite algumas coisas da máquina virtual, mas outras coisas como quais programas serão instalados e as configurações dos mesmos não são feitas diretamente pelo Vagrant.  
Os programas que são responsáveis por isso são chamados de "Provisioning", os 3 principais que trabalham bem com o Vagrant são: Shell (simples shellscripts que devem ser executados), [Chef](http://www.opscode.com/chef/ "Chef") e [Puppet](http://puppetlabs.com/puppet/puppet-open-source "Puppet Open Source"). Vou falar aqui sobre o Puppet.

### Puppet

Para configurar os programas no Puppet é bem interessante. Ao invés de se descrever as configurações de forma imperativa, você descreve usando uma forma declarativa. Ex (traduzido de:

**Me Faça um Sanduiche! (Imperativo)**  
Espalhe manteiga em uma fatia do pão. Deixe essa fatia no prato com a face para cima;  
Espalhe requeijão em uma outra fatia de pão. Coloque esta fatia em cima da primeira, com a face voltada para baixo;  
Me traga o sanduiche;

**O Sanduiche Que Eu Quero. (Declarativo)**  
Deve haver um sanduiche no prato na minha frente em 5 minutos;  
Este deve ter apenas manteiga e requeijão entre as duas fatias de pão;

*Esses exemplos foram baseados nos exemplos do post a seguir: [From Imperative to Declarative System Configuration with Puppet](http://spin.atomicobject.com/2012/09/13/from-imperative-to-declarative-system-configuration-with-puppet/ "From Imperative to Declarative System Configuration with Puppet")*

Assim, fica muito mais simples configurar suas dependências, além disso o Puppet possui diversos [Módulos](https://forge.puppetlabs.com/ "Puppet Forge") já prontos para diversas aplicações, basta usa-los e configurar os detalhes.

\[adsense\]

Instalando Tudo
---------------

Primeiramente deve-se instalar o VirtualBox, que será o responsável pelas Maquinas virtuais criadas pelo Vagrant.  
Para isso basta ir no site do VirtualBox, e procurar o release compatível com seu Sistema Operacional:  
[Download VirtualBox](https://www.virtualbox.org/wiki/Downloads "Download VirtualBox")

Agora é necessário instalar o Vagrant, para isso vá ao site de downloads do Vagrant, e baixe a ultima versão e release que seja compatível com seu Sistema Operacional: [Download Vagrant](http://downloads.vagrantup.com/ "Download Vagrant")

Por fim devemos instalar o Puppet, para isso existem instruções bem completas no [site](http://docs.puppetlabs.com/guides/installation.html#installing-puppet-1 "Instalar o Puppet"), para cada tipo de plataforma.  
É importante entender que nesse tipo de cenário, o que você deseja instalar é o **Puppet Standalone**  
Vou colocar aqui a maneira em que instalei o Puppet Standalone no meu Ubuntu 12.04. Para isso executei os seguintes comandos:

``` {lang="shell"}
    wget http://apt.puppetlabs.com/puppetlabs-release-precise.deb
    sudo dpkg -i puppetlabs-release-precise.deb
    sudo apt-get update
    sudo apt-get up
    sudo apt-get install puppet-common
```

Isso vai instalar o Puppet Standalone em sua máquina, mas faltará fazer algumas ultimas configurações para ele ficar 100%. Entretanto, como desejo usar o Puppet apenas para instalar facilmente os Módulos (mencionados anteriormente) no Vagrant, não é necessário terminar a configuração do mesmo.

*Para os curiosos: essa configuração tem haver com alterar alguma coisa no cron-tab, conforme a [documentação](http://docs.puppetlabs.com/guides/installation.html#with-cron "Terminar de configurar Puppet Standalone")*

Agora já tem tudo pronto pra você começar seu projeto com o Vagrant e o Puppet.

Exemplo Simples
---------------

Vamos criar uma maquina virtual, e instalar nela os pacotes: **build-essential, vim, curl e git-core**.  
E vamos fazer com que toda vez que a máquina for ligada, esta execute updates com o apt.

### Vagrantfile

Primeiramente, dentro da pasta do novo projeto, usamos o comando:

``` {lang="shell"}
$ vagrant init
```

Em seguida deixamos o conteúdo do arquivo com a seguinte cara:

``` {lang="ruby"}
# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "precise64.box"
  config.vm.box_url = "http://files.vagrantup.com/precise64.box"

  # definimos um ip para essa máquina (usando NAT aqui).
  config.vm.network :private_network, ip: "192.168.56.101"

  config.vm.provider :virtualbox do |vb|
    # esse é um bug conhecido ao usar NAT em alguns casos no virtualbox, ele fica sem dns
    # e pra resolver isso colocamos essa linha
    vb.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]

    # Colocando mais memoria e mudando o nome da maquina virtual
    vb.customize ["modifyvm", :id, "--memory", 1024]
    vb.customize ["modifyvm", :id, "--name", "treinamento_ej"]
  end

  # Garante que o apt-get update é rodado antes das configurações do puppet
  # tive que fazer isso, outra vez por conta do dns não aparecer para o Puppet
  config.vm.provision :shell, :inline =>
    "if [[ ! -f /apt-get-run ]]; then sudo apt-get update && sudo touch /apt-get-run; fi"

  # definindo configurações do puppet
  config.vm.provision :puppet do |puppet|
    # pasta onde fica seus manifests
    puppet.manifests_path = "manifests"

    # arquivo manifest que você quer que seja chamado de começo
    puppet.manifest_file  = "mymanifest.pp"
    
    # pasta onde ficam os modulos do puppet
    puppet.module_path = "./modules"

    # melhor logging do puppet na execução do vagrant, é bom pra debugar coisas
    puppet.options = "--verbose"
  end
end
```

### Manifests do Puppet

Como descrito no arquivo Vagrantfile, devemos criar nosso arquivo **mymanifest.pp**, dentro de uma pasta chamada **manifests**, e este será o ponto de partida para as ações do Puppet:

``` {lang="shell"}
$ mkdir manifests
```

e dentro desta nova pasta criada o arquivo **mymanifest.pp** deve ter o seguinte conteúdo:

``` {lang="ruby"}
group { 'puppet': ensure => present }
Exec { path => [ '/bin/', '/sbin/', '/usr/bin/', '/usr/sbin/'] }
File { owner => 0, group => 0, mode => 0644 }

class {'apt':
  always_apt_update => true,
}

package { [
    'build-essential',
    'vim',
    'curl',
    'git-core'
  ]:
  ensure  => 'installed',
}
```

### Instalando Módulos do Puppet

No arquivo mymanifest.pp utilizamos o módulo APT do Puppet, portanto devemos instala-lo na pasta modules do projeto.  
Devemos primeiro criar essa pasta:

``` {lang="shell"}
$ mkdir modules
```

Em seguida rodamos o comando:

``` {lang="shell"}
$ puppet module install puppetlabs/apt --modulepath modules
```

Isso fará o download desse módulo e de suas dependências (nesse caso o stdlib) dentro da pasta recém criada.

### Rodando Tudo

Para terminar e ter sua máquina pronta, basta usar o comando:

``` {lang="shell"}
$ vagrant up
```

Isso carregará sua máquina virtual e em seguida irá chamar o mymanifest.pp, que por sua vez dá instruções ao Puppet da maquina virtual do que deve ser feito.

Caso deseje acessar sua máquina virtual, basta executar o comando:

``` {lang="shell"}
$ vagrant ssh
```

Assim você fica logado como o usuário vagrant e pode fazer o que bem entender dentro da máquina.

Outra coisa interessante, é que a pasta do seu host (máquina real) onde tem o arquivo Vagrantfile, fica sendo uma pasta compartilhada com a nova máquina virtual no caminho **"/vagrant/"**. Ou seja: todo código fonte que houver dentro da pasta do projeto, irá aparecer também dentro da máquina virtual na pasta "/vagrant/". Que moleza, não?

Caso queira consultar melhor o código desse exemplo, ele encontra-se disponível no github: <https://github.com/arruda/exemplo-vagrant-puppet>

Abraços!
