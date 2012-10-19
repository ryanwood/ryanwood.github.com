---
layout: post
title: "Crontab Problems With Nano"
date: 2007-06-02 15:03
comments: true
tags: [cron tips]
---
I was trying to set up a cron job on my new (relatively) [SliceHost](http://slicehost.com) VPS. On Ubuntu, each time I would run `crontab -e`, edit and save the file, I would get this:

> "/tmp/crontab.nQMgF1/crontab"\:2: bad minute  
> errors in crontab file, can't install.  
> Do you want to retry the same edit?  

It didn't seem to matter that the syntax was correct. Ha. After googling around for a while, I found out that the problem was with nano, the default text editor on Ubuntu. It wraps long lines by default and crontab has a problem with this.To fix the problem you need to turn off long line wrapping which is on by default. Go to **/etc/nanorc** and uncomment the following line

    set nowrap

Now, nano will correctly save your crontab. (I also uncommented 

    set rebinddelete

to find a problem with backspace/delete on the mac.)