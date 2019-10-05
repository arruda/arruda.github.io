Title: Sharing Files Easily With Python
Date: 2013-04-01 19:42
Author: arruda
Category: programação, Python, Selecionados, Web
Tags: files, oneline, python, server, sharing
Slug: sharing-files-easily-with-python
Status: published

Want to share some files in a folder from your unix OS to others PCs on the same network, without having to install any other library, just Python?

Simple HTTP Server
==================

There is a simple command that lets you create a very basic HTPP server in the current folder, and it's just one line!

``` {lang="python"}
python -m SimpleHTTPServer 8000
```

This will run a local server using the port 8000 to the current dir(from where you run this command).

Then I'll you need to do is get your IP and access it in a browser from another PC, ex:  
**192.168.0.5:8000**

And then you just navigate and download the files from the browser, simple as that!

So if I want to share the contents of the folder: **/home/my\_user/some\_folder**, just enter this folder,  
and run the **simpleHTTTPServer** in there!

\[adsense\]

Using an alias
--------------

You can even set a alias on your bash\_rc(or similar) to make it easier, ex:

``` {lang="shell"}
alias share_local = 'python -m SimpleHTTPServer 8000'
```

Then all you'll have to do is:

``` {lang="shell"}
share_local
```
