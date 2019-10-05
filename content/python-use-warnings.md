Title: Python: Use Warnings!
Date: 2013-10-17 10:13
Author: arruda
Category: programação, Python
Tags: deprecated, example, future, import, python, runtime, syntax, use, warning
Slug: python-use-warnings
Status: published
Attachments: wp-content/uploads/2013/10/warning.jpeg

Have you ever confronted a code like this:

``` {lang="python"}
# shouldn't use this function anymore! Now use XYZ!
def some_old_function(arg1,arg2):
    return arg1 + arg2
```

This is something that I see too often, and this could be done better.  
\[adsense\]

Warnings
--------

There is something in python called **warnings**, and guess what? The name is very intuitive, they warn about something, kind like an Exception, but they just warn you...

There are some types of warnings, the example above could be rewritten as follows:

``` {lang="python"}
import warnings
# shouldn't use this anymore!
def some_old_function(arg1,arg2):
    warnings.warn(
        "shouldn't use this function anymore! Now use XYZ.",
        DeprecationWarning
    )
    return arg1 + arg2
```

This way, when this function is called (maybe there was a piece of the code that hadn't got refactored and you missed it)  
you'll get the warning in the sys.stderr (by default, but in some cases you can change this to another output).

You might be asking: **"Why the hell won't you just delete this function?"**  
Well, because in some cases you just can't be sure that this function isn't been called by someone else in the project, sometimes you're in the middle of a large refactoring that is going on slowly.

### Other Warning Types

Here are other useful warning types:

#### SyntaxWarning

This is a warning about dubious syntactic features, for example:

``` {lang="python"}
import warnings

def some_function(arg1,arg2):
    
    # Not sure if this is the best approach for this case, maybe should do arg1 - arg2...
    warnings.warn(
        "Should confirm what's the best approach for some_function",
        SyntaxWarning
    )
    return arg1 + arg2
```

This way if you somehow forgot about this dubious syntax, the warning will remind you of it.

#### RuntimeWarning

This is a warning about dubious runtime features, for example:

``` {lang="python"}
import warnings

def some_function(array,position):
    
    # better verify if I can access array[position] first
    if position < array.lenght:
        return array[position]
    else:
        warnings.warn(
            "Tried to access a position that doesn't exist in array inside some_function."
            ,RuntimeWarning
        )
        return 0
```

#### FutureWarning

This is a warning about constructs that will change semantically in the future, for example:

``` {lang="python"}
import warnings

# Probably there will be another arg in the future in this function
def some_function(arg1,arg2):
    warnings.warn(
        "Lookout! In the future there will be an arg3 argument for some_function",
        FutureWarning
    )
    return arg1 + arg2
```

So if you're planning to change the constructor then it's a good idea to put one of these.

#### ImportWarning

For warnings during the process of importing a module  
**  
dont\_use\_this\_module.py**:

``` {lang="python"}
import warnings
# this module shouldt be imported, please... don't use it...
warnings.warn(
   "Please, don't import the module 'dont_use_this_module'.",
    ImportWarning
)
```

This warning will be sent if anyone try:

``` {lang="python"}
import dont_use_this_module
```

.

#### PendingDeprecationWarning

Very similar to DeprecationWarning, but in this case the feature is not yet deprecated,  
but soon (maybe in the next version of the project) will.

``` {lang="python"}
import warnings
# shouldn't use this anymore!
# in version 2.1 and above this will be deprecated
def some_almost_old_function(arg1,arg2):
    warnings.warn(
        "Shouldn't use this function anymore! It will be deprecated in version 2.1. Use function 'xyz' instead",
        PendingDeprecationWarning
    )
    return arg1 + arg2
```

That's all, if you want to know more about warnings you can read the docs here: [Python Warnings Doc](http://docs.python.org/2/library/warnings.html "Python Warnings Doc").
