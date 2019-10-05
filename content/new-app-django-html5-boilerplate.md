Title: New App: Django HTML5 Boilerplate
Date: 2013-12-27 06:06
Author: arruda
Category: Django, programação, Python, Selecionados, Web
Tags: app, boilerplate, Django, django-h5bp, h5bp, html5, template
Slug: new-app-django-html5-boilerplate
Status: published

Hi there, and a late **Happy Merry Christmas** for all of you!

So, you may wonder what I did in this great time of the year, and the answer is: **A new Django app.**

Django-H5BP
-----------

This is a **reusable** Django app that is **very simple** and helps a lot.

The idea is that instead you grab the HTML5 boilerplate and make it fit your new project base template, for every project, you just install this app, extend it's predefined HTML5 Boilerplate template and change the blocks that you want to.  
\[adsense\]

### Installing

Very simple, just use pip:

``` {lang="shell"}
$ pip install django-h5bp
```

Then inside yours project **'installed\_apps'** settings:

``` {lang="python"}
INSTALLED_APPS = (
    ...
    'django_h5bp',
)
```

### Using it!

Now that you have it installed in your project, you just need to **extend** the  
**'h5bp.html'** template in your **base** template, just changing the blocks that you want.  
Here is a **simple example** for your **"base.html"** template:

``` {lang="html"}
{% extends "h5bp.html" %}

{% block page-title %}My Great Project{% endblock %}

{% block header %}
    Here is my page header
{% endblock %}

{% block main-container %}
    
        Hello World!
    
{% endblock %}

{% block footer %}
    Footer
{% endblock %}
```

What else?
----------

### Static Files

The default HTML5 boilerplate static files (js, css) are also included and using the **{{ STATIC\_URL }}** instead of a fixed path.

But the HTML5 boilerplate's **default "favicon.ico"** file is **not present**, since it would override yours depending on the position that you set this app in the "installed\_app" list, so I removed it. This way you just need to put your **own favicon.ico** that it will already be loaded in the template.

### 404 Page

I also added the **default 404.html** page to the project, but this one **has no template blocks**, just the original HTML5 Boilerplate 404 page.

### Template Blocks

There are some template blocks predefined to help you customize your page with lesser work, there are blocks for meta tags like **"title" and "description"**, for **Jquery.Document.Ready** section, **google analytics** and more!  
You can checkout the full list here:  
[Django-H5BP Template Blocks](https://github.com/arruda/django-h5bp#h5bp-template-blocks "Django-H5BP template blocks")

Contributing
------------

If you find something interesting, or some bug, or juts want to say hello to the code, here is the github repository:  
[Django H5BP Repository](https://github.com/arruda/django-h5bp "Django H5BP Repository").

That's all folks,  
and a **happy new year**!
