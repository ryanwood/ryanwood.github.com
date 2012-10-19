---
layout: post
title: "Ubuntu Hardy Lts Slice With Nginx, Passenger, Git, Vlad And More!"
date: 2010-01-15 18:41
comments: true
tags: [slice server deployment ngnix ubuntu passenger git]
---
I finally did it. I took notes as I built a server and am posting it (mainly so I don't forget). In case someone wants to print this, I left most of the URLs in text so you'd be able to read them. So here it goes.

I am doing this on [Slicehost](http://slicehost.com) and decided to user Ubuntu Hardy 8.04.2 as the OS maily for the long term support.

Core Setup
=======

Initial Config
----------

<http://articles.slicehost.com/2008/4/25/ubuntu-hardy-setup-page-1>
<http://articles.slicehost.com/2008/4/25/ubuntu-hardy-setup-page-2>

Ruby Enterprise Edition, Nginx, Passenger
---

I followed this great guide:

<http://antoniocangiano.com/2009/11/20/setup-ruby-enterprise-edition-nginx-and-passenger-aka-mod_rails-on-ubuntu/>

Gems
---

The latest version of rubygems was install after install REE.

    sudo gem update --system
    sudo gem update

Install all the gems I normally use. Just too many to list.

Create/edit ~/.gemrc with

    gem --no-ri --no-rdoc

<http://docs.rubygems.org/read/chapter/11>

Git
---

If you use aptitude, you get an old version 1.5.4.x

<http://serengetisunset.wordpress.com/2009/02/28/installing-git-1613-on-ubuntu-804/>

I did this to get the newest version installed. You need the build dependencies for it to work.

    sudo apt-get remove git-core
    wget http://kernel.org/pub/software/scm/git/git-1.6.6.tar.gz
    sudo apt-get build-dep git-core
    tar xvzf git-1.6.6.tar.gz
    cd git-1.6.6/
    ./configure --with-tcltk
    make
    sudo make install
    
Source: <http://brunomiranda.com/past/2008/5/12/deploying_github_repository_with_vlad>

MySQL
----

<http://articles.slicehost.com/mysql>

    sudo gem install mysql

*Migrate existing datbase from Heroku*

1.  sudo gem install taps
2.  Copy your existing .heroku directory from your dev box to the deploy server.
3.  Create your production db
4.  rake db:migrate to get all the struct created
5.  Pull that db down. For the prayerthread app:

        heroku db:pull --app prayerthread mysql://root:pass@localhost/prayerthread_production

<http://adamblog.heroku.com/past/2009/2/11/taps_for_easy_database_transfers/>

Mail
----

<http://articles.slicehost.com/email>

<http://articles.slicehost.com/2008/7/28/email-preparing-the-slice>
<http://articles.slicehost.com/2008/7/29/postfix-installation>
<http://articles.slicehost.com/2008/7/31/postfix-basic-settings-in-main-cf>

Good reference if you're setting up a full scale mail server:

<http://articles.slicehost.com/2008/9/2/mail-server-slice-setup>

Deployment
==========

Cobbled deploy recipe using:

<http://dennisbloete.de/blog/rails-deployment-with-vlad-git-and-passenger>
<http://snippets.aktagon.com/snippets/264-Vlad-deployment-recipe-for-Phusion-Passenger>

Deployment Issues
-----------------

There were 3 of them:

1.  Vlad error

         Usage: /usr/bin/git-submodule [--quiet] [--cached] [add [-b branch]|status|init|update|summary [-n|--summary-limit ] []] [--] [...]
         rake aborted!

    The issue is because Hardy has an older version of git 1.5.x. Once I upgrade to 1.6, it is fine.

    There was a [commit](http://github.com/jbarnette/vlad-git/commit/f6f98fd994a12848b619fd5a82df355b348ac69b)
    to fix this but it wasn't yet in the gem. 
    I manually patched the gem file. to address 
    [the](http://github.com/jbarnette/vlad-git/issues#issue/1)
    [issue](http://github.com/jbarnette/vlad-git/issues#issue/2).

2.  Cloning from a remote git repo

    This is an issue when cloning from unfuddle.com (or github.com). You need 
    an ssh key to run vlad from the local box to the deploy server, but then vlad 
    executes the clone from the deploy server so an additional key pair is needed.
    I looked at setting up ssh forwarding, but [these directions weren't clear enough
    for me](http://jordanelver.co.uk/articles/2008/07/10/rails-deployment-with-git-vlad-and-ssh-agent-forwarding/).
    couldn't find clear enough directions.

    Instead, I just created a deploy key pair and uploaded the pub key to unfuddle. That
    authenticated me but since I am connecting over a non-standard port, I still had an issue.
    
3.  SSH Config for non-standard port
  
    On the deploy box, I needed to tell SSH to use the standard port to connect to unfuddle.
    Add the following to `~/.ssh/config` as noted [here, under theSSH Config section](http://github.com/guides/addressing-authentication-problems-with-ssh):
    
        Host sourcescape.unfuddle.com
          Port 22
          Hostname sourcescape.unfuddle.com
          IdentityFile ~/.ssh/unfuddle_rsa
          TCPKeepAlive yes
          IdentitiesOnly yes
