---
layout: post
title: "The Rails Difference"
date: 2006-01-29 12:36
comments: true
tags:
---
There's a lot of hype about [Rails](http://www.rubyonrails.com) these days. Most of the chatter compares Rails to .NET, Java, PHP, etc. Though those are valid and often interesting discussions, I  think they often miss the most unique difference.

That difference is what the average programmer spends much of their time doing: upgrading and deploying  applications. Let's face it. You only launch an application once, but you (or someone else) will be maintaining and upgrading it forever (... well, at least for longer than you expect to). I don't see any communities addressing this nearly as aggressively and ambitiously as Rails.

It is very evident that Rails was built by developers in the trenches, by those living and breathing in the real world of maintaining applications. Microsoft just released ASP.NET 2.0 and VS2005. With all the new bells & whistles, they still don't offer a solid solution for deployment and data migrations.

*Side Note:* _I also love the fact that Microsoft only offers unit testing tools in the Enterpri$e version. Brilliant! Take a excellent open source tool, nAnt, integrate it into your product and then charge through the nose for it. Now that's business model!_

Enter Rails answer to these two issues: seemless database upgrades with [Migrations](http://wiki.rubyonrails.com/rails/pages/UnderstandingMigrations) and simply yet powerful deployments using [SwitchTower](http://manuals.rubyonrails.com/read/book/17.) Keep on the lookout for follow-up posts on each of these killer tools.