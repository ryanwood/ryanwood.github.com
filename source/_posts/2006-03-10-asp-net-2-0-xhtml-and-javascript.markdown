---
layout: post
title: "Asp.Net 2.0, Xhtml, And Javascript"
date: 2006-03-10 10:55
comments: true
tags:
---
I never cease to be amazed by good ole' MS. At [work](http://www.datastream.net) we've been going through the pain of moving from ASP.NET 1.1 to 2.0. They claim that ASP.NET 2.0 is at least XHTML transitional compliant, but beware!

If, in an attempt to be an efficient, compliant coder, you add a javascript include to the <code><HEAD></code> tag using XHTML formatting, form buttons on your page will no longer work.
<pre><code><script type="text/javascript" src="/search/search.js"/></pre></code>
That's right, no post back occurs. You can click and click but the page never gets submitted. Low and behold, once you change it back to the old school method, things work again.
<pre><code><script type="text/javascript" src="/search/search.js"></script></pre></code>
Go figure.