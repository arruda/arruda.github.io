Title: Review: Eclipse + Django + VirtualEnv
Date: 2012-01-16 10:01
Author: arruda
Category: Django, programação, Python, Selecionados
Tags: Django, Eclipse, IDE, pydev
Slug: review-eclipse-django-virtualenv
Status: published
Attachments: wp-content/uploads/2012/01/pydev_banner2.gif

Hi there everyone, I'd like to share with you some of my experience with Eclipse as a IDE for Django and virtualEnv.  
First of all I already tried some other IDEs, like VIM, TextMate, PyCharm and Gedit(that I still used 'till now), but for many reasons I just preferred a simple Text Editor.

VIM
---

Why not?  
Well, I've the power it has, and all that stuff, how it's fast and etc...  
But the point is that if you want to use this as a working tool, you'll need to train in that(a lot) to make it right. And since I couldn't expend the time necessary to learn every single shortcut(I still dream of doing this \*-\*) this one was out.

TextMate
--------

Now it's the time that all the macboys start shouting that I need to buy a mac since it's the most perfect, awesome, incredible OS ever... And I can understand, but I left TextMate out as my main IDE for to reasons:  
It doesn't have the resource of **ctrl + click to navigate in a function/attribute/class**(I'll explain this latter on).  
And more important of all:  
I'm prefer a PC scenario that I have a linux system(WORK) and a windows shitted system(GAMES), and no, mac still can't play games... **Sorry Mac, but you lake my sense of having fun gaming.**

PyCharm
-------

Ok, this one at first promised a lot, but I don't know if I was the only one that have this problem, but this IDE took me some long time to run, and do all the stuff(even more than Eclipse!!).  
But that was not the real deal, the problem was that when we where starting to get along the IDE simply stoped, telling me that I should by a license(it was only a Shareware edition).  
And, for what I read I could even use it as a IDE if my project where a open source.  
**"Ok"** I thought, but if by some reason I want to do a parallel project that is not Open Source, I'll need to buy a license?!  
**"Hummm.. no thanks, I prefer to find another FREE tool"**  
And that was the end for PyCharm.

Gedit
-----

After all that I just fall back for Gedit(a normal text editor in Ubuntu) and a terminal... But some days ago I thought of given Eclipse(PyDev) a try.  
And so this is what I got from Eclipse:

Eclipse(PyDev)
==============

First I'm using the PyDev plugin for eclipse, in a Classig Eclipse installation.

Pros
----

And right at the start there are already plenty of good reasons to use this IDE:

-   Code Completion(Including code for your project!)
-   Debug(Nice one within Eclipse)
-   Code Navigation(Ctrl + click in a function/class/method will that you to that code in a blink, and then you can go back using another shortcut)

Cons
----

Ok, not everything is a "sea of flowers", there are some problems in there, the first one is how it deals with VirtualEnv:

-   You need to configure what's the python interpreter for that **WORKSPACE**, so if you want to have a separated python interpreter for each project you'll need to set a different workspace for each project.
-   Another problem is that if you have some more complex things in your project (like a different directory organization) will probably have problem with eclipse telling you that your project is full of errors).

Solutions
---------

-   For the errors that will pop in your face if your project is not in the normal django structure, you can just set the Eclipse option to stop checking errors(for eclipse there will be still erros, but for the most tools there will be no problems).
-   For the PYTHON\_PATH thing, I got a great help from **[Brian Jinwright](http://www.arruda.blog.br/programacao/review-eclipse-django-virtualenv/#comment-208 "Solution to workspace") **That said that:

> <div>
>
> "You don’t have to create a new **Workspace** for each project/virtualenv. If you go to the **Project** menu and select **Properties**, then choose **PyDev – Interperter/Grammar**, then choose **Click here to choose an interperter not listed** then choose the virtualenv interperter that you want."
>
> </div>

 

<div>

</div>

 

That's all, hope you enjoy.
