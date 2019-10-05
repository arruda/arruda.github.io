Title: Trac + Git + Post-receive Hooks
Date: 2012-09-04 13:24
Author: arruda
Category: Ambiente de Trabalho, Web
Tags: 0.12, git, gitolite, hooks, locale, post-receive, script, trac
Slug: trac-git-post-receive-hooks
Status: published
Attachments: wp-content/uploads/2012/09/trac_git.jpg

I'm just documenting this since I just made it work(again) in my test server, but need to implement this in my work.  
I just had some headache since I lost the first server I implemented this, and didn't have it documented anywhere, so now I'll post here what worked for me, and some problems that I faced, and maybe this will help somebody else.

But, after I started writting this post I just asked myself: "Why not make a Script that does all that I need?". And so I did:

The Script
----------

The idea of this script is prepare a ambient with:

-   TRAC 0.12(with locale)
-   GIT server (Using Gitolite)
-   New Trac Project and Git Repository
-   Working Post-receive Hook integration for the new Repository and TRAC Tickets

The requirements
----------------

You'll need root permission to the Server or simillar.  
SSH acess to the server (OpenSSH for example)  
A working station (Another machine apart from the server, preferably your desktop or laptop).

Preparing the Script to Run
---------------------------

First you'll need to copy your's workstation RSA key to your Server(you can copy anywhare, ex: "/tmp/")

``` {lang="shell"}
scp ~/.ssh/id_rsa.pub root@DOMAIN_NAME:/tmp/myNewUser.pub
```

**Note that the name of the RSA key must be the SAME name of the user you whant to have as the admin for the GIT server and the TRAC Project that will be created.**

After this you can download the script into anywhere, ex:

``` {lang="shell"}
cd /tmp
wget https://github.com/arruda/TRAC-GIT-HOOKS/tarball/master
tar -zxvf master
cd master
```

Running the Script
------------------

First of all the script is divided in two parts. That's because you have to do some manual configurations in the workinstation in the middle of the process.

### First Script

``` {lang="shell"}
./install_1.sh PROJECT_NAME REPO_NAME DOMAIN_NAME USER_NAME USER_PSSWD RSA_FOLDER_PATH
```

Replacing with your own configurations as follow:

-   PROJECT\_NAME: is the name of your project, ex: MyTrac
-   REPO\_NAME: is the name of your repository, ex: mynewrepo
-   DOMAIN\_NAME: your domain, ex: mysite.com
-   USER\_NAME: your username, ex: myNewUser (THIS MUST BE THE SAME USER NAME OF THE RSA KEY BEFORE!)
-   USER\_PSSWD: your password, ex: mystrongpass
-   RSA\_FOLDER\_PATH: the path to the folder where you put the rsa pub key, ex: /tmp

Using the example above this would be a possible usage:

``` {lang="shell"}
./install_1.sh MyTrac mynewrepo mysite.com myNewUser mystrongpass /tmp
```

Configuring the GIT server
--------------------------

This has to be done in your workstation after the fist part of the install:

``` {lang="shell"}
git clone git@DOMAIN_NAME:gitolite-admin
```

replacing DOMAIN\_NAME with your server domain.

Open the conf/gitolite.conf file, and add this lines to the end of it:

``` {lang="shell"}
repo REPO_NAME
    RW+    =    USER_NAME
```

replacing REPO\_NAME and USER\_NAME with the ones used in the execution of the script, ex: myNewUser.

Save, commit and push it.

``` {lang="shell"}
git add . 
git commit -m 'new repo' 
git push origin master
```

Finishing the Install
---------------------

After this execute install\_2.sh, using the same parameters as before! Ex:

``` {lang="shell"}
./install_2.sh MyTrac mynewrepo mysite.com myNewUser mystrongpass /tmp
```

This will finish the TRAC project creation and the GIT configuration for the new repository.

Also will install and configure the post-receive hook that allows you to **close and reference tickects in the commit messages.**

Helping
-------

If you want to help, feel free to fork the project on github:  
<https://github.com/arruda/TRAC-GIT-HOOKS>

That's all folks
