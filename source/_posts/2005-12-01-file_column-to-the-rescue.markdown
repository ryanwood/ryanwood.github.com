---
layout: post
title: "File Column To The Rescue"
date: 2005-12-01 07:00
comments: true
tags: [rails, plugins]
---
I haven't had much time to post lately as I have been working late nights on a consulting project for a small publishing company in town. Last night I needed to build a image upload feature into the site. Well...actually another image upload feature. I had already build the functionaity for one area yet it wasn't abstracted enough for reuse.

Striving to maintain the [DRY](http://wiki.rubyonrails.com/rails/pages/DRY) princple, I started look for another approach and I came across [file\_column](http://www.kanthak.net/opensource/file_column/) written by [Sebastian Kanthak](http://www.kanthak.net/index.html.) WOW!

First off let me say that plugins in Rails 1.0rc are incredible. No only did I get the feature implemented, but now I have all the additional ability to do thumbnails and other [RMagick](http://rmagick.rubyforge.org/) effects. Thanks Sebastian!

Yet again, what would have taken hours, if not days, with .NET, I completed in minutes due to flexibility and simplicity of Rails and the availability of open source.