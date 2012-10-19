---
layout: post
title: "Bye Bye Vlad"
date: 2010-01-21 18:23
comments: true
tags: [vlad capistrano deploy]
---
I was initially enamored with the [capistrano][cap] like features, yet simplicity of [Vlad the Deployer](http://rubyhitsquad.com/Vlad_the_Deployer.html). I spent 2 days getting the "simplifed deploy" working. Well, I thought it was anyway. Turns out that it wasn't deploying the correct version from git.

I found a [bug in Vlad](http://github.com/jbarnette/vlad-git/issues#issue/1) which was fixed in master, but wasn't in the gem. Then I found another bug in the [vlad-git](http://github.com/jbarnette/vlad-git). It turns out [ktheory](http://github.com/ktheory/) had forks of each with the bugs fixed, but with different gems. I tried to use those, but still wasn't getting the expected results.

*This is simplicity?!?!*

I never had any issue with [capistrano][cap]. So I went back to old faithful. In 10 minutes, I was back to the beauty that is:

    cap deploy

Here are a coupleparting thoughts on Vlad:

* I understand why they broke out all the plugins, but it was a hassle to deal with
* There was virtually no feedback as to what Vlad was doing during a deploy. I much prefer capistrano's output on deploy.

[cap]: http://www.capify.org