---
layout: post
title: "Improving By Gits And Bounds"
date: 2009-06-20 08:23
comments: true
tags: [git development]
---
Subversion (SVN) has been a staple of my development process since I ran kicking and screaming out of the Visual SourceSafe (VSS) dungeon many years old. It has served me very well. I used the basic edit-commit-merge life-cycle and all was good. Here’s the strange thing.

**I didn’t really learn how to use subversion specifically, or really version control in general, until I quit using subversion and started using git.**

The evolution started with VSS. Essentially it was a code backup. We did the occasionally file rollback, but that was it. Write code and periodically check it in, comment-less of course. I had a brief affair with SourceGear Vault. It was a much improved replacement for VSS.  Though it fixed a lot of the bugs and other issues in VSS, but as I move more away from the Microsoft world, it became less useful.

Enter subversion.

What a breath of fresh air. Edit-merge-commit. Open source. Quicker. Concurrent development. Nice. Then I started learning about branches and tags. Wow, those could be useful. “Could” being the important word. Using branches and merging in SVN is certainly possible, but trivial. So I used them occasionally, but never with confidence or as any core part of my development process.

Then the cool kids started chanting “git, git, git”.

So I checked out what all the fuss was about like any good hopelessly addicted to new technology freak would do. Git was hard and a bit scary. Yeah, the whole “clone, add, commit” thing was fine, but start talking about rebasing and my head hurt. Git 101 tutorials will only take you so far and the rest you have to learn in the trenches.

I’m a few months out now and I wouldn’t go back. Oh wait. I have to. I still have a slew of projects in SVN. As I go back to those projects, I’m using SVN in ways I never would have previously.

Yesterday I had a bug to fix in a production app on Rails 2.0.1. It has been running without issue for over a year. So I go into my dev machine to make a quick fix and realize that I started to upgrade the app to 2.1.0 about 6 months ago. I have 6 or so commits but never deployed any of the changes. I can’t deploy them because they were never finished. mmmm.

Before git, I’d probably just make the changes on the server and back the code into the trunk. Gong. Being much more comfortable with branching and merging from working with git, I simply created a stable-1.0 branch off of the revision that was last deployed, applied the changes there. A quick update to my deploy.rb file pull from the branch rather than trunk and then`cap deploy`. Done.

My point of this ramble is that choosing to work with new (different) technologies matures you as a developer. And the things you learn will give you a new, and generally better, perspective even when you work within your wheelhouse.