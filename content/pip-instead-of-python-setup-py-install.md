Title: PIP instead of python setup.py install
Date: 2013-03-21 22:07
Author: arruda
Category: programação, Python
Tags: pip, python, setup.py
Slug: pip-instead-of-python-setup-py-install
Status: published

\[adsense\]  
A nice way to install any package that has it's setup.py file is to use the **pip install -e command**:

``` {lang="python"}
pip install -e .
```

**OBS: Use this in the same directory that has the setup.py file**

This way you can have it nicely controlled by PIP =)
