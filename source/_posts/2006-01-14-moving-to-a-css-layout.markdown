---
layout: post
title: "Moving To A Css Layout"
date: 2006-01-14 03:10
comments: true
tags:
---
For the past 3 years or so, there has been a shift in the web design field away from table based layouts toward the nirvana of standards-based, xhtml compliant, CSS driven layout. It is often a frustrating topic for those that have used tables for layout (pretty much every designer/developer I know). So most, despite noble intentions, end up doing a hybrid design (tables & CSS) or simply abandon CSS layout all together using CSS solely for formatting.

Well, times are changing and this task is getting slightly easier. With the new browsers (e.g. Firefox 1.x -- get it and use it!), there are _far less_ cross browser issues though some still exist. Here are some resources that I hope you find helpful:

* [Tips on CSS Layout](http://blogs.vertigosoftware.com/jatwood/archive/2006/01/06/Guidelines_and_Tips_for_Pure_CSS_Layouts.aspx) (thanks Jason!)
* [Simple columned layouts by Lissa](http://www.lissaexplains.com/css3.shtml
*) [Ten more CSS tricks you may not know](http://www.webcredible.co.uk/user-friendly-resources/css/more-css-tricks.shtml

Also,) a side note on Firefox. It has a couple phenomenal extensions to help in this area:

* The [Web Developer Toolbar](http://chrispederick.com/work/webdeveloper/) is invaluable. Just install it.
* [Aardvark](http://www.karmatics.com/aardvark/) lets you alter a web page on the fly, view partial source, delete elements for printing, and many more goodies.
* [IE Tab](https://addons.mozilla.org/extensions/moreinfo.php?application=firefox&category=Popular&numpg=10&id=1419) lets you open up IE within a tab in Firefox and see how the page will render without ever opening IE.

Hopefully you can start using CSS layout s in your app. The power is amazing. One thing that forced me to do this on a recent project was the print-friendly requirement. I wanted to hide both the header and menu areas when printing. With tables, I was stuck, but transitioning to a CSS based layout, it now works like a charm.