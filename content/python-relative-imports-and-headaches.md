Title: Python - Relative Imports and Headaches
Date: 2014-03-04 16:12
Author: arruda
Category: programação, Python, Selecionados
Tags: absolute import, error, future, import, non-package, problem, python, relative
Slug: python-relative-imports-and-headaches
Status: published

Just got my hands on the great book "**Two Scoops of Django - Best Pratices for Django 1.6**" and decided to put in pratice one of their advises: **The Relative Imports**.

\[adsense\]

Whooo Relatives Imports, that's great!
--------------------------------------

Yep, pretty neat stuff. If you always is afraid of obscuring a absolute package with a relative one when using import, than this is what you were looking for.

But it's not that easy to set up at first, you need some tricks that are not well explained in [PEP 366](http://legacy.python.org/dev/peps/pep-0366/ "PEP 366").

"Attempted relative import in non-package" Error
------------------------------------------------

Yes... if you're just starting on relative imports then you will come across this.

You may also come across this other error: **"Parent module XXXX not found while handling absolute import"** and many other errors because a confusion in how exactly you have to set up your package to work with relative imports.

So I decided to explain what you have to set up, to have a package that can handles relative imports nicely.  
Lets start by listing what has to be done, and in the end I'll give you an example in Github.

The main idea is this: Considering you have a **my\_package**, with **submodule1** and a **my\_pyscript.py** (the Python script that is going to be executed to do whatever your package does)

With that in mind, this is what you'll have to set in **"my\_pyscript.py"** to be able to use relative imports in this package:

### Back to the future

Put at the beginning of the file:

``` {lang="python"}
from __future__ import absolute_import
```

That way you can that advantage of the way Python 3 deals with the import.

### sys.path

If you don't have your package in the **sys.path** (if you're still developing a package then you probably won't have) then you have to put it in there.

### Add the Package to sys.modules

To do this, you can just do a simple 'import my\_package', or, you can import the module and add it to the sys.modules too (not quite sure of what's the difference).

### Set the \_\_package\_\_ option

After this, you just need to set the **\_\_package\_\_** option to **'my\_package'**.

### Have fun

After this, you can use relative imports like:

``` {lang="python"}
from .submodule1 import *
```

Example Project
---------------

Here is an example project on Github that implements what was described earlier.  
[Relative Import Example](https://github.com/arruda/relative_import_example "Relative Import Example")

That's all, hope this helps you guys!
