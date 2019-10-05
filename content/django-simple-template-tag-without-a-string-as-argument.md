Title: Django - Simple Template Tag Without a String as Argument
Date: 2012-12-08 10:03
Author: arruda
Category: Django, programação, Python, Selecionados, Web
Tags: argument, Django, simple, simple_tag, tag, template
Slug: django-simple-template-tag-without-a-string-as-argument
Status: published

I've never been too much into template tags, since as far as I could understand from the [django docs](https://docs.djangoproject.com/en/1.3/howto/custom-template-tags/ "Django template tag docs"), was only possible to get a simple template tag if passing a string as parameter.  
But now I see that's not true.

Simple Tag
==========

<p>

If you take a look at the docs you'll find an example like this:  

<script src="https://gist.github.com/4220855.js?file=simple_tag_string.py"></script>
</p>
<p>

That's something nice, you can also change it a little, to just add something to the context:  

<script src="https://gist.github.com/4220855.js?file=simple_tag_string_context.py"></script>
</p>

Different Argument. Is it Possible?
===================================

You see... at first I thought that any method decorated by **"\@register.simple\_tag"** needed to have a string as argument.  
But no, I just found out that you can use any parameters there, for example:

Let's say you want to use in the templates a method from a **Poll's** model that requires a user as argument.  
You can do it like this:

<p>
<script src="https://gist.github.com/4220855.js?file=polls_tags.py"></script>
</p>
<p>

Then in your template you would do as follows:  

<script src="https://gist.github.com/4220855.js?file=sometemplate.html"></script>
</p>

That's it, hope this will help out anyone that was in doubt about if it's possible to make a simple\_tag without a string as argument =)
