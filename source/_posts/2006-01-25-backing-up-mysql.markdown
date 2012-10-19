---
layout: post
title: "Backing Up My Sql"
date: 2006-01-25 15:08
comments: true
tags:
---
After committing the cardinal sin on a recent project of killing the production database without a backup the day before launch, I spent some serious time figuring out a solid back up solution. Thankfully I found [automysqlbackup](http://sourceforge.net/projects/automysqlbackup/.) Thought the name lacks creativity, the script rocks! It's a unix shell script that creates 5 running daily, weekly, and monthly backups of multiple MySQL databases in a very clean directory structure. It's highly recommended if you are doing anything with MySQL.

Oh, and thankfully, the host had a backup of the database as of 1am that night. Whew!