---
layout: post
title: "Premature Extraction"
date: 2006-11-15 08:33
comments: true
categories: [rails, architecture]
---
[The Rails Way](http://www.therailsway.com) is off with their first code review. It is really great to see into the coding process of top notch hackers. Their [first review](http://www.therailsway.com/2006/11/15/tracks-part-1) deals with "acts\_as" code modules and "premature extraction". [Koz](http://www.koziarski.net/) keeps it simple.

bq. These both illustrate a common anti-pattern I see with rails programmers: premature extraction. Just because rails has a bunch of meta programming magic with names like acts_as_list, doesn’t mean you need it.

The process is all about keeping it simple and extracting only when you need to. I've been learning more and more about that in a Ruby application I've been working on lately. It is a challenge, especially coming from .NET, to not overly abstract early.