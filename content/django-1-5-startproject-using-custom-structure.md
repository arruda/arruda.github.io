Title: Django 1.5 - Startproject Using Custom Structure
Date: 2013-03-10 20:21
Author: arruda
Category: Django, programação, Python, Selecionados, Web
Tags: custom, Django, project, start, startapp, startproject, template
Slug: django-1-5-startproject-using-custom-structure
Status: published

Hi there, I decided to make this post, to explain how I'm using this great feature of Django (1.4 and higher).

Simple Usage
============

<p>

This is just the simplest example of how you can use it:  

<script src="https://gist.github.com/arruda/4546833.js?file=simple_cmd.sh"></script>
</p>

This will give you this layout:

``` {lang="shell"}
myproject/
    manage.py
    myproject/
        __init__.py
        settings.py
        urls.py
        wsgi.py
```

Beyond the basic
----------------

That is a pretty nice layout... but after some time you start to do more elaborated stuff, or simply just want things more on your way.

So now you can just use the **--template** option lets you specify a directory, file path or URL of a custom project template.

<p>

For example, I have a directory that has this structure with some pre-defined files:  

<script src="https://gist.github.com/arruda/4546833.js?file=my_structure.txt"></script>
</p>
<p>

Then I can just use a simple command to re-use this structure:  

<script src="https://gist.github.com/arruda/4546833.js?file=template_cmd.sh"></script>
</p>

The **--extensions** options let me pass what files will be "used" as a template( don't try to put the html extension, it will crash on you), the rest will just be copied as it is, without having it's content "rendered". See this in the docs, for some [help](https://docs.djangoproject.com/en/dev/ref/django-admin/#render-warning "render warning")  
I recommend adding the **md** for the README.md file in the **extensions**.

\[adsense\]

The next level
--------------

You can also, as I said before, pass the url of a **.tar** file of a project template.  
So, you could do something like I did:

-   Create a github repo for the project directory
-   Zip this folder and add it to the repo
-   Create an alias that will always start a project using this repo as the project template.

<p>

If you want to use a github repo, you could use this next command:  

<script src="https://gist.github.com/arruda/4546833.js?file=http_cmd.sh"></script>
</p>
<p>

You can just run this next command, to add an alias called **djproj** and another **djapp** to your **.bashrc**:  

<script src="https://gist.github.com/arruda/4546833.js?file=other.sh"></script>

  
**Don't forget to replace my github repository for your's!**  
This way you can now just do:

</p>

``` {lang="shell"}
djproj myproject
```

That it will use the repository project template.

If you want to take a look at how can your project template be, just checkout my [github repository](https://github.com/arruda/dj_project_templates "My Django Proejct Templates").

StartApp
--------

You can do the same thing for the **startapp** command, so you can also create some custom app layouts!

That's it, hope this helps you =)
