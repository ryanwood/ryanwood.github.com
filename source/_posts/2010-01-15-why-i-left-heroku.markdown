---
layout: post
title: "Why I Left Heroku"
date: 2010-01-15 13:46
comments: true
tags: [heroku deployment hosting]
---
I love [Heroku](http://heroku.com), I really do. They have eliminated nearly all of the hassle surrounding  deployment and server management in the Ruby/Rails world. Here's the rub...

*They are simply not affordable for the little guy.*

"But Ryan", you say, "what about the free plan?" The [Blossom-1](http://heroku.com/pricing#blossom-1) plan is great and you do get a lot of value (including some really great [free add ons](http://addons.heroku.com/)). The problem come when the site starts to grow.

The free plan is basically  [loss leader](http://en.wikipedia.org/wiki/Loss_leader) -- "a product sold at a low price (at cost or below cost) to stimulate other, profitable sales." It is how they _draw you in_, and draw you in they do. It is an awesome service.

As soon as you need to grow the site just a bit, the price jumps significantly. It's a great value at the entry level and, as best I can tell, for larger scale sites as well. It's the smaller site with little to no revenue that feels the punch.

Let's get specific. I'm starting a new project and my choice was Heroku at $0/mo or [Slicehost](http://slicehost.com) (who completely rocks as well) at $20/mo for 256MB VPS. A no-brainer. I chose Heroku. It was easier, simpler, and far less work.

A couple weeks later, I have some beta users and want to roll out a new notification feature that will require some background processing. To get 2 application processes ([dynos](https://heroku.com/how/dynos)) and run a background job, the price jumps from $0 to ~$72/mo (2 dynos + 1 worker = [Blossom-3](https://heroku.com/pricing#blossom-3)). If the database grow beyond 5MB, the I would need to move to [Koi-3](https://heroku.com/pricing#koi-3) at ~$87/mo. 

Pretty soon I need to send more than 200 emails per month so I need to add the SendGrid Premium add-on for $20/mo bringing the total up to ~$107/mo. On the Slicehost side, I have to do all the work of setting up, configuring, and maintaning the server, BUT I am still paying $20/mo. I may need to ramp up to the the 512MB slice but I'm still at only $38/mo.

That's an estimated ~$69/mo savings. When you are bootstrapping a small project, that it significant.

Let me reiterate, I *love* heroku. I wish there was a plan that was more reasonable at the lower end. Since there is no comparable path on the Heroku side, I've decided to migrate the project back to [Slicehost](http://www.slicehost.com/).

Stay tuned for my notes on building an Ubuntu slice. I'm going to document it this time. Really. I will.