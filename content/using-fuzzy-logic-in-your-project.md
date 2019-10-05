Title: Using Fuzzy Logic in Your Project
Date: 2011-07-28 11:30
Author: arruda
Category: Aleatoriedades, Java, programação, Python, Selecionados
Tags: fuzzy, Java, libraries, logic, pyfuzzy, python, web, xfuzzy
Slug: using-fuzzy-logic-in-your-project
Status: published
Attachments: wp-content/uploads/2011/07/xfuzzy.gif, wp-content/uploads/2011/07/pythonlogo.png, wp-content/uploads/2011/07/fuzzy_logic.gif

From Where This Came From?!
---------------------------

After a few months working with fuzzy logic in my work, I was able to see it's purpose in a project.  
And that's not only limited to working with prodution planning(like this [GESPLAN](http://ead.deap.int.gov.br/course/view.php?id=12 "Gesplan") project that I'm working on), you can use it with many other purposes.  
I'm not going much further in what you can do with it, if you want to learn more about it, here is a link to start: <http://www.fuzzy-logic.com/>.

Fuzzy Libraries
---------------

Ok, now the real deal:  
If you want to use fuzzy in a **Java** based project, I advise you to use:

### [XFuzzy - Java](http://www2.imse-cnm.csic.es/Xfuzzy/)

[![]({static}wp-content/uploads/2011/07/xfuzzy.gif "xfuzzy"){.alignleft .size-full .wp-image-545 width="218" height="65"}]({static}wp-content/uploads/2011/07/xfuzzy.gif)  
This one is not just a integration of Java with fuzzy, it's(using their own description):

> ...a set of tools that ease the user to cover the several stages involved in the design process of fuzzy logic-based inference systems, from their initial description to their final implementation.

If you want you can generate a ASCII file(that represents your fuzzy system) using it, then you can generate it source code to some languages(like C++ and Java). Finally just need to get this generated files and use them like some libraries(expecific to your .xfl file).

\[adsense\]

### [PyFuzzy - Python](http://pyfuzzy.sourceforge.net/)

[![]({static}wp-content/uploads/2011/07/pythonlogo.png "pythonlogo"){.alignleft .size-full .wp-image-547 width="149" height="148"}]({static}wp-content/uploads/2011/07/pythonlogo.png)  
Now for this **Python** library I can't tell much, since I never really used this one, but for what I've read this one has some good points.  
Differently from XFuzzy, it doesn't have a intuitive GUI to help you build your fuzzy systems, you need to do them by hand.  
But since they have some nice examples, you won't just be let all alone with your code to do your work.

### Using Generic Fuzzy Systems

If your system uses generic fuzzy systems, you would have a problem with xFuzzy, since it generates the source files based on a expecifc system.  
So if you want to use generics, you would need to insert xFuzzy sources into your own project(remembering that XFuzzy sources are in Java language) and then create a inference engine to deal with the fuzzyfication and defuzzyfication of your .XFL(the ASCII files that represent your system) files.  
In the pyfuzzy, you already have to make some code for each system you want, but I don't know if they already have some ease way to work with generic.

That's it folks, soon I'll post some more infos of how to use the xFuzzy into a Java Web project, based on what we've implemented on GESPLAN, so keep tuned.

**PS:**For those who want a PT-BR tutorial for Fuzzy Logic, here is a good place to start: <http://condicaoinicial.com/2010/04/tutorial-de-logica-fuzzy-1.html>
