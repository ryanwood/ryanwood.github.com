---
layout: post
title: "Git   Making The Switch"
date: 2009-05-28 02:54
comments: true
tags: [git]
---
I am using [git] for all new projects. For the active ones that are still on [subversion] I'm using [git-svn]. It is true-- git-svn is a [gateway drug][3]. While git provides a number of [advantages over subversion][4], there are a number of hurdles to overcome if you decide to switch. 

## Command Line

One of the toughest areas, is getting comfortable with the command line. Most of the subversion users I know rarely, if ever, use the `svn` command line utility. The simply stick with a nice GUI client. When learning git I would argue that you _need_ to learn the command line. If you don't understand what is going on under the covers, you can really end up in a ditch. The [documentation][5] is pretty good, but unless you are a command line junkie, it will take some time to move your version control mindset over.

And make sure you keep your install current. There has been [lots of good stuff][1] added in recent days.

## It Takes Thought

The power of git comes at the price of understanding. Version control becomes more than a simple "right-click and commit every once in a while" endeavor. Git allows you to craft your commits so your repository is clean and tells a story of how your app developed. Using rebase you can rewrite, combine, remove and edit commits. It crazy and dangerous and comes with significant responsibility, but the price is worth it. [Check this out][6].

## Confidence

The biggest hurdle for me was gaining confidence that I could be productive and wasn't going to destroy my applications inadvertently. The resources available are getting [better][git] and [better][gitcasts] and [better][gitready]. However, confidence only comes with experience. It doesn't matter how many books you read on dating, at some point, you have to walk up to that personal and ask them out. Confidence requires action. Luckily, git won't throw a drink in your face or laugh at you.

If you're on a steady diet of svn, [compare][7] and give git a try. You know you want to.

[1]: http://jasonrudolph.com/blog/2009/05/27/git-up-10-reasons-to-upgrade-your-old-git-installation/
[gitready]: http://gitready.com/
[git]: http://git-scm.com/
[gitcasts]: http://www.gitcasts.com/
[subversion]: http://subversion.tigris.org/
[git-svn]: http://www.kernel.org/pub/software/scm/git-core/docs/git-svn.html
[3]: http://www.robbyonrails.com/articles/2008/04/10/git-svn-is-a-gateway-drug
[4]: http://whygitisbetterthanx.com/#svn
[5]: http://git-scm.com/documentation
[6]: http://blog.madism.org/index.php/2007/09/09/138-git-awsome-ness-git-rebase-interactive-?cos=1
[7]: http://git.or.cz/course/svn.html