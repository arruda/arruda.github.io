Title: Django-Celery In Daemon
Date: 2012-04-09 11:58
Author: arruda
Category: Django, programação, Python, Selecionados, Web
Tags: celery, celeryconfig, celeryd, CELERY_CONFIG_MODULE, daemon, Django, django-celery, init.d
Slug: django-celery-in-daemon
Status: published
Attachments: wp-content/uploads/2012/04/images.jpg

Hello everyone, I'm doing this post because I just got stuck in this a while ago and thought it would be nice to share.

Django-Celery
-------------

<p>

First of all you need to install it and configure the basics(this all is well explained in the [docs](http://django-celery.readthedocs.org/en/latest/getting-started/first-steps-with-django.html)), so basically you can do:  

<script src="https://gist.github.com/2343490.js?file=install.sh"></script>

  
Then you need to install a broker server(like RabbitMQ):  

<script src="https://gist.github.com/2343490.js?file=broker.sh"></script>

  
After this is done, you need to put some basic configurations for celery in your settings file, like this:  

<script src="https://gist.github.com/2343490.js?file=settings.py"></script>

  
Also don't forget to run **syncdb** or **migrate**(if using south).

</p>
<p>

Now if you want to run celery, you do it like:  

<script src="https://gist.github.com/2343490.js?file=run.sh"></script>
</p>

Daemonizing...Not so fast!
--------------------------

This part is not so intuitive for those who are starting to use this tool, but after you get what need to be done, it's all fast and furious.  
This is, in my opinion, because of some misleading details in the [celery daemon docs](http://docs.celeryq.org/en/latest/cookbook/daemonizing.html). So I'll try to make it as explained as I can.

\[adsense\]

### Create a Configuration File For The Daemon

In this file there will be some variable used to run the celery as a daemon, like:  
Where is the project folder;  
How many workers;  
Where will be the log files...  
And many others.

But it will also contain any **environment variable** that you need in your project!  
So if you have a different settings for development and for production using an env var, you'll have to set this in the configuration file as well.  
**Or else you'll might and up having the celery working with the sqlite3.**

<p>

You create this file as: **/etc/default/celeryd**  
And put something like this inside it:  

<script src="https://gist.github.com/2343490.js?file=conf.sh"></script>
</p>

### Get a init.d script

Yeah, this is strange, but after some time I understood this.  
So basically the file that they tell you to run in the docs, you need to get and put it there yourself...  
And this init.d script will run the celeryd using the configurations that you'll set in the **/etc/default/celeryd**.

You can get the file in:  
<https://raw.github.com/ask/celery/1da3aa43d1e6de525beeda398d0acb8841d5b4d2/contrib/generic-init.d/celeryd>

This file must go to **/etc/init.d/celeryd**  
And don't forget to make it executable: **chmod +x /etc/init.d/celeryd**

Using the Daemon
----------------

<p>

To use it, just do like this:  

<script src="https://gist.github.com/2343490.js?file=daemon.sh"></script>
</p>

### Some Details

So, if you run the celery without the daemon and have no problem, but when running the daemon it tells you that **some celery table was not created**, then probably your celeryd is not using the correct [database](#env_var).

Also don't forget that the **CELERYD\_USER** and **CELERYD\_GROUP** must have permission to use the **manage.py**, and to access the **CELERYD\_LOG\_FILE** and **CELERYD\_PID\_FILE** folders!

And of course. You need to create the folders for **CELERYD\_LOG\_FILE** and **CELERYD\_PID\_FILE**.

And again, don't change the **CELERY\_CONFIG\_MODULE="celeryconfig"**. Since you're using django-celery there is no **celeryconfig.py** in your project, but you need to set this so that it will get the default one(that it's in the celery package).

That's it! Hope this will help others that were lost in this(especially in the **CELERY\_CONFIG\_MODULE**) and in the **init.d script**.
