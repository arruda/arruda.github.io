Title: Docker - 3 Quick Tips
Date: 2014-07-24 01:02
Author: arruda
Category: Ambiente de Trabalho, programação, Selecionados, Web
Tags: 3, aufs, debugging, devicemapper, docker, filesystem, nsenter, ssh, tips, vagrant
Slug: docker-3-quick-tips
Status: published
Attachments: wp-content/uploads/2014/07/baby-36828_640.png

[![Docker](http://www.arruda.blog.br/wp-content/uploads/2014/07/baby-36828_640-300x164.png){.aligncenter .size-medium .wp-image-2352 width="300" height="164"}]({static}wp-content/uploads/2014/07/baby-36828_640.png)  
I'm reading and testing a bit about this new tool ([Docker](https://www.docker.com/ "Docker website")), and after some time I discovered some **tips** that I wanted to share with you guys.

\[adsense\]

1 - Check out other containers filesystems
------------------------------------------

Maybe for what you plan on installing inside a container, the default filesystem that Docker uses (**AUFS**), ins't the best choice.  
A pretty good example is a **MySQL** DB image, that has a problem [already documented](https://github.com/dotcloud/docker/issues/783 "unexpected file permission error in container").  
But don't be alarmed, there is a workaround for this!  
You just need to [change your Docker filesystem to Device Mapper](http://muehe.org/posts/switching-docker-from-aufs-to-devicemapper/ "Switching from AUFS to device mapper in docker").

2 - Debugging Containers With Nsenter
-------------------------------------

If you want to debug your containers, and don't feel very well installing a SSHD inside each container just to navigate inside it, then you should use Nsenter.  
This allow you to get a prompt inside your container that has a process initialized, and it doesn't hurt the Docker principle (**one concern per container**).

You can read more about this in here: [If you run SSHD in your Docker containers, you're doing it wrong!](http://jpetazzo.github.io/2014/06/23/docker-ssh-considered-evil/ "If you run SSHD in your Docker containers, you're doing it wrong!")

3 - Test things with Vagrant!
-----------------------------

Had problem installing Docker in your machine?  
Or maybe you just want to test this new tool in a clean environment?  
That's easy, since the guys from Phusion created a base Vagrant image that has it's a kernel ready to install docker.

So all you have to do is

``` {lang="shell"}
$ vagrant init phusion/ubuntu-12.04-amd64
```

And you'll have a Vagrantfile ready to go.

More info on this in here: [Docker-friendly Vagrant base boxes](https://github.com/phusion/open-vagrant-boxes "Docker-friendly Vagrant base boxes")

That's all, and have fun playing with Docker!
