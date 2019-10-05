Title: CloudFuzzy - The Online Fuzzy Toolbox Solution
Date: 2014-03-18 18:14
Author: arruda
Category: Django, Java, Python, Selecionados, Web
Tags: api, cloud, Django, fuzzy, github. restfull, inference, Java, online, play, pyfuzzy, python, scala, solution, system, toolbox, xfuzzy
Slug: cloudfuzzy-the-online-fuzzy-toolbox-solution
Status: published
Attachments: wp-content/uploads/2014/03/fuzzy_system.jpg, wp-content/uploads/2014/03/cf_fill.png

Hi there. I decided to make a post about this project that I've recently released a beta version.  
Basically this project started inside this other project that I was doing in my work: [Gesplan](http://gesplanblog.int.gov.br/ "Gesplan Project").

\[adsense\]

What's this about?
------------------

The main feature of **CloudFuzzy** is to help you create a new **fuzzy inference system** and to help you test **online and friendly interface**.  
\[gallery\]

What technologies are behind it?
--------------------------------

The project was made using **[Play 2.0.2](http://www.playframework.org "Play Framework")**, a Java and Scala web framework in the web part, and for the fuzzy engine was used the core of **[XFuzzy 3.0](http://www2.imse-cnm.csic.es/Xfuzzy/Xfuzzy_3.0/index.html "XFuzzy 3.0")** library.

Where is it going?
------------------

The idea is to make **CloudFuzzy** a **web-service** using a **RESTfull API**.

But I'm also trying to **rewrite** the hole system in **Python**, using **[Django](https://www.djangoproject.com/ "Django Web Page")** as the web framework and **[pyfuzzy](http://pyfuzzy.sourceforge.net/ "Pyfuzzy on Sourceforge")** for the fuzzy engine.

Wait, what?! Rewrite it in Python?
----------------------------------

Yeap, that's right, and here is the reason why:  
Even though Play is very simple and powerful it's still more focused on Scala, so the docs for Play using Java aren't as good as the Scala docs.

And come on, I'm not going to struggle with some framework when I can use one that I'm more interested in (like Django), so there's already a branch for it in the Github repository.

I'd like to contribute, what do I do?
-------------------------------------

Just fork the repository [here](https://github.com/arruda/cloudfuzzy "CloudFuzzy Github"), and if you prefer the Django framework, just as I do, then use [this branch](https://github.com/arruda/cloudfuzzy/tree/django "CloudFuzzy Django Github").

That's all for now.
