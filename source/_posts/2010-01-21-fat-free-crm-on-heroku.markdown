---
layout: post
title: "Fat Free Crm On Heroku"
date: 2010-01-21 18:34
comments: true
tags: [fatfreecrm heroku deploy]
---
I created a [fork on github](http://github.com/ryanwood/fat_free_crm) to ease deployment of [Fat Free CRM](http://www.fatfreecrm.com/) to [Heroku](http://heroku.com/). I found this [great post](http://saturnflyer.com/blog/jim/2009/09/08/fat-free-crm-on-heroku/) about doing this very thing, but I wanted something a little simpler.

For the impatient, here's the quick Heroku install:

    $ git clone git://github.com/ryanwood/fat_free_crm.git
    $ heroku create
    $ git push heroku master
    $ heroku rake crm:setup USERNAME=myusername PASSWORD=mypass EMAIL=my@email.com

Essentially, all I've done in this fork (as of this writing) is:

1. Remove all of the stylesheet and javascript caching directives
2. Fix a minor issue in the `config/config.ru` file

You can always check it out [at the wiki](http://wiki.github.com/ryanwood/fat_free_crm/installation-on-heroku).

_UPDATE: Sept 20, 2010_

> I've updated [my heroku-friendly fork on github](http://github.com/ryanwood/fat_free_crm) to use version 10.1 of FFC. Let me know if you have any issues. Thanks.