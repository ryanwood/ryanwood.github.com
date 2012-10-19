---
layout: post
title: "Git Cherry To The Rescue"
date: 2009-06-05 06:02
comments: true
tags: [git]
---
I've been trying to find a simple way to find out the commit differences in two git branches for while now. I resorted to using `git show-branch` which works pretty well, but can get cumbersome when you have a lot of branches. I just discovered [`git cherry`](http://kernel.org/pub/software/scm/git/docs/git-cherry.html) is just want I've been looking for.

This will show the commit differences between my-dev-branch and master.

    $ git checkout my-dev-branch
    $ git cherry -v master
    + cf9221200cb9574e3cc92fa72570f9813b86af24 Moved configuration out of lib folder
    + 32c456574cb58a2a8c9b354b5eca56b6f28bab82 Fixed some bugs

I guess It pays to start digging deeper into the underlying git commands.