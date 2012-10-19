---
layout: post
title: "Ajax Framework Comparison"
date: 2006-02-01 10:39
comments: true
tags:
---
With all the buzz about AJAX, it's important to look at the frameworks that are being built to handle the xmlhttp abstraction. [Milan Negovan](http://www.aspnetresources.com) wrote a  [nice little comparsion](http://www.aspnetresources.com/blog/prototype_vs_atlas.aspx) between [Prototype](http://prototype.conio.net/,) an open source javascript library (built into Rails) and [Atlas](http://www.asp.net/default.aspx?tabindex=7&tabid=47,) Microsoft's (yet to be released) abstraction layer. Here's his conclusion:

bq. Atlas and Prototype each has its own groove. I expect server-side developers to gravitate more toward Atlas although the sheer payload of it will be punishing to the end user. I anticipate UI, usability and accessibility craftsmen to choose Prototype to build on.

After playing with both, I feel that prototype is much cleaner, leaner, and more extensible approach. It does however force developers to get deeper into the code and have a better understanding of client-side javascript. Atlas, however, seems to abstract the developer from the details of the code. This is classic Microsoft. "Just drag this and we'll write the code for you." It also moves client-side scripting into server-side objects. If you enjoy dragging and dropping rather than coding, then Atlas may be for you. The other downside of Atlas is that, based on the VS2005/ASP.NET 2.0 time to market, we won't see a production release for (most likely) years. That really puts a damper on things.

If you're into (or getting into) any type of AJAX development, it would server you well to get to know what you are building on.