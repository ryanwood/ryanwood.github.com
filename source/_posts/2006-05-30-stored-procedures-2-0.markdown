---
layout: post
title: "Stored Procedures 2.0?"
date: 2006-05-30 06:19
comments: true
tags:
---
Coming from a Microsoft platform background, I'm well versed in the stored procedure mantra, which practically equates to "use them everywhere". Over the past year or so, I've starting [questioning that assumption](http://codebetter.com/blogs/jeremy.miller/archive/2006/05/25/145450.aspx.) While stored procs are useful, they do more to add unneccessary complexity to application development.

[Jeff Atwood](http://www.codinghorror.com/blog) offers up a compelling (yet slightly dated) argument for reducing the scope of stored procs in his post [Who needs Stored Procedures, anyways?](http://www.codinghorror.com/blog/archives/000117.html)

bq. For modern databases and real world usage scenarios, I believe a Stored Procedure architecture has serious downsides and little practical benefit. *Stored Procedures should be considered database assembly language: for use in only the most performance critical situations.* There are plenty of ways to design a solid, high performing data access layer without resorting to Stored Procedures; you'll realize a lot of benefits if you stick with parameterized SQL and a single coherent development environment.

I now longer use stored procs when working with  an [application database](http://martinfowler.com/bliki/ApplicationDatabase.html.) They become much more useful when dealing with an [integration database](http://martinfowler.com/bliki/IntegrationDatabase.html.) [Martin Fowler](http://www.martinfowler.com/) captures the [differences](http://martinfowler.com/bliki/DatabaseStyles.html.

The) real question to ask is, "Where am I spending my time?". Am I doing application development where I can [encapsulate my business logic](http://codebetter.com/blogs/jeremy.miller/archive/2005/06/09/129562.aspx) into a single application layer? Or am I working with a database that multiple application must interact with where a clear business layer nearly impossible to maintain?

Though I still have a foot in both worlds, I have gravitated over the past few years toward much more application development. I simply enjoy it more. Hence, I find myself using stored procs less and less.