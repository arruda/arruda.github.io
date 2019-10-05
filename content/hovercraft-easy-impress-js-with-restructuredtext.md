Title: Hovercraft - Easy Impress.js with reStructuredText
Date: 2013-05-14 14:41
Author: arruda
Category: Aleatoriedades, Python, Selecionados, Web
Tags: easy, hovercraft, impress.js, js, python, reST, reStructuredText
Slug: hovercraft-easy-impress-js-with-restructuredtext
Status: published
Attachments: wp-content/uploads/2013/05/rc_hovercraft-thumb-419x300-565146.gif

Hi there, long time without posting, but now I\`m back with the review of this nice tool:  
**Hovercraft**, a tool for creating (easily) a nice [Impress.js](http://bartaz.github.io/impress.js/ "Impress.js") presentation from a [reStructuredText](http://en.wikipedia.org/wiki/ReStructuredText "reStructuredText").

What\`s impress.js?
-------------------

[Impress.js](http://bartaz.github.io/impress.js/ "Impress.js") is a great JS presentation framework based in CSS3 transforms/transitions and many other cool stuff.

What\`s reStructuredText?
-------------------------

This is a lightweight markup language that is most used in documentation of software such as Docutils and that is easily readable by humans.

So.. Hovercraft...
------------------

What [Hovercraft](http://regebro.github.io/hovercraft/ "Hovercraf") does is simplify the creation of a Impress.Js presentation.  
So, instead of making tha HTML/CSS yourself, all you have to do is a ReStructuredText and run hovercraft, that the corresponding HTML/CSS and JS will be generated for you =)

Installing Hovercraft
---------------------

To install it, just install it using PIP:

``` {lang="shell"}
pip install hovercraft
```

**OBS:**Hovercraft is intended to be used with Python 3. But I also made it work(at least what I could test) in Python 2.7.  
If you want to use it with Python 2.7 you\`ll also need to install configparser:

``` {lang="shell"}
pip install configparser
```

\[adsense\]

Basic Usage
-----------

First of all you\`ll have to create a **.rst** file for your presentation. Ex:  
**helloworld.rst**.

Then inside you put:

``` {lang="rst"}
:title: Hello World!

This is a simple Hello world example for hovercraft!

----

This is the First Slide:
========================

Some text here in this slide...

.. note::

    Here whe have some notes for this slide.

----

Second Slide
============

Hello World!
```

### Generate the Presentation

To create a Impress.js presentation from the last example, just do:

``` {lang="shell"}
hovercraft -a helloworld.rst helloworld
```

This will create a directory named **"helloworld"** that contains the HTML, CSS and JS for your presentation, you just have to open the index.html and present!

Adding some nice Effects
------------------------

You can use many effects in your presentation, and set many options:

In the next example we\`ll set so that :

-   when moving from the first slide to the second, it will go down.
-   in the transition from the second to the last, it will rotate 90 degrees.

So here is the ReStructuredText for this new presentation:

``` {lang="rst"}
:title: Hello World! Efx

This is a simple Hello world example for hovercraft! with some effects.

----

This is the First Slide:
========================

Some text here in this slide...

.. note::

    Here whe have some notes for this slide.

----

:data-y: r1000

Second Slide
============

Hello World!

----

:data-rotate: 90

Rotating
========
Nice!
```

Again, just run the same command:

``` {lang="shell"}
hovercraft -a helloworld.rst helloworld
```

And you\`ll get a presentation with rotation and custom positioning.

More!
-----

If you want to know more about this too, and what it allows you to do, just check it\`s presentation: <http://regebro.github.io/hovercraft/>
