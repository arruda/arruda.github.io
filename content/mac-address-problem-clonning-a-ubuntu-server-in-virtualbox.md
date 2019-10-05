Title: Mac Address Problem - Clonning a Ubuntu Server in VirtualBox
Date: 2012-09-21 00:04
Author: arruda
Category: Selecionados, Web
Tags: clone, mac, macadress, server, ubuntu, VM
Slug: mac-address-problem-clonning-a-ubuntu-server-in-virtualbox
Status: published

What problem?
-------------

If you have already tried to clone a VM in VirtualBox you have the option to reset all the Mac Address(what is something logical to do).

But if you try that in a Ubuntu Server... well.. you're doomed!

How to do it then?
------------------

Well, first you need to do just as you would, go ahead and clone a VM, but **don't reset all the MACs!**

After this, you will need to shutdown your original VM (since you didn't reset the MAC and you don't want some MAC conflict in your network, do you?)

After a it has cloned(completely) the VM, you should start you new cloned VM.  
It should start and act just like the original one, if not, well, then that's another problem, not the MAC Address.

Then shutdown the Cloned VM, go into it's network options and click in the button that generates a new MAC Address. Copy this number, but **DON'T CLICK OK!**. Cancel this and start the VM.

### Why is the MAC change a Problem?

I'm not an expert in this, so the therms that I use might not be the best ones, but it seems that  
when you change that address it's like you removed fisically the network device, and now it's trying to find the old one but it's only finding this new one in the "fisically"(because it's virtual) location of the old one.

So you'll have to edit the file that tells you about the MAC address of the eth0 or anyother network device that you're using.

To do so, edit the file:

``` {lang="bash"}
 
vim /etc/udev/rules.d/70-persistent-net.rules
```

And where you read, for exemple:

``` {lang="bash"}
ATTR{address}=="00:00:00:00:00:00"
```

replace the address(in this example its the **"00:00:00:00:00:00"**, but in your case will probably different) for your new Mac Address(the one you just copied before).

Remember to put the ":" separating the MAC in Six pairs, and with low caption letters.  
So this: **"080025EA9011"** becomes this **"08:00:25:ea:90:11"**

Save the file and shut down the VM.

Now go again in the VM network configuration and set the mac to be this new one: **"080025EA9011"**. And now click ok.

Reboot, and everything should be working.
