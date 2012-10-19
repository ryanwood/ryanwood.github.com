---
layout: post
title: "Whenever: Cron...The Ruby Way"
date: 2009-06-11 05:16
comments: true
tags: [cron ruby]
---
Many Rails app need to make use of cron in some form or fashion. [Whenever](http://github.com/javan/whenever/tree/master) is a great little DSL for creating, organizing, managing, and deploying your app related cron jobs. 

Here's an example from the [wiki](http://wiki.github.com/javan/whenever/instructions-and-examples). You simply install the gem and run `wheneverize` in your root dir. Then add the following to your `config/schedule.rb` file:

    set :path, '/var/www/apps/my_app' 

    every 10.minutes do
      runner "MyModel.some_process" 
      rake "my:rake:task"  
      command "/usr/bin/my_great_command" 
    end

will yield...

    0,10,20,30,40,50 * * * * /var/www/apps/my_app/script/runner -e production "MyModel.some_process" 

    0,10,20,30,40,50 * * * * cd /var/www/apps/my_app && RAILS_ENV=production /usr/bin/env rake my:rake:task

    0,10,20,30,40,50 * * * * /usr/bin/my_great_command


For more on setup and deployment, see the [README](http://github.com/javan/whenever/tree/master). RubyInside has a [nice review](http://www.rubyinside.com/whenever-a-ruby-dsl-for-defining-cron-jobs-1835.html) as well.