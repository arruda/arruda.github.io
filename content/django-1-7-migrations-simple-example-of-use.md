Title: Django 1.7 Migrations - Simple Example of Use
Date: 2014-07-31 23:33
Author: arruda
Category: Django, Python, Selecionados
Tags: 1.7, Django, example, makemigrations, migrate, migration, models, simple, syncdb, use, workflow
Slug: django-1-7-migrations-simple-example-of-use
Status: published

Hi there, since **Django 1.7** release is coming soon, I decided to take some time and learn how the workflow will be when working with these **Migrations**, and decided to share my experience with you.

\[adsense\]

New Commands
------------

So, first of all we have the

``` {lang="shell"}
./manage.py migrate
```

that replaces the old

``` {lang="shell"}
./manage.py syncdb
```

This is the command that will **execute** the migrations, and create the initial Django tables (for auth, session and etc). But you should see now that the **superuser** for the DB **is not created** with this.  
So you have to create it using the command:

``` {lang="shell"}
./manage.py createsuperuser
```

Another command that appeared is the

``` {lang="shell"}
./manage.py makemigrations
```

and he is the one that will **create the migration** files representing the changes in your models.py.

So the **basic idea** is:

1.  Modify models.py
2.  Make the migration with: **makemigrations**
3.  Execute the migration with: **migrate**

A Workflow Example
------------------

I created a git repository([django-17-migrations-example](https://github.com/arruda/django-17-migrations-example "django-17-migrations-example Repository")) that has a simple workflow of what you'll probably face when doing your projects.

In it you'll be see a simple **Polls** app using migration, all you have to do is navigate through the commits and execute the migrations.  
I use **Scheme Migrations** and **Data Migrations**, and also implement a simple **rollback** for a custom made migration.

You can check the complete workflow and let it guide you, in the [Readme](https://github.com/arruda/django-17-migrations-example#workflow "Workflow instructions") of the project.

That's it guys.  
**Good migrations** for you.
