---
layout: post
title: "Git Workflow: Merge Or Rebase"
date: 2010-03-14 08:09
comments: true
tags: [git development]
---
One of the things that I'm passionate about is the development process. So much of the battle is won or lost by the type of development process you have. Leaning on a [couple][1] [smart][2] guys, I've established a very clean workflow in git. If you haven't read these posts, please do so before continuing. Both are excellent and will help clarify my question.

The only discrepancy between them is how to handle feature branches. Should you interactively rebase (`git rebase -i`) your feature branch to one commit (or possibly a couple)?  [Rein][1] takes this approach. [Vincent][2] on the other hand prefers to leave the feature branch intact and do a non-fast forward  merge (`git merge --no-ff feature`) to merge the feature back into the develop branch.

I've tried it both ways. Neither is right or wrong and both have their advantages.

Both go into the develop branch as a single commit, one as a normal commit and one as a merge commit. With the interactive rebase, you lose the granular commit history and potentially have a significantly larger commit. But you have a clear comment (with summary bullets if you follow Rein's suggestion) as to what the commit it.

With a forced merge commit, you maintain the feature branch history which is nice to track down where some error entered the code, but the merge commit is auto-commented with something like '`Merge branch 'feature-x'`'. It's less clear when looking down the commit list of develop what is represented. Another downside of this approach is that you create a lot of unnecessary merge commits in the tree.

At this point, I think I lean more toward the interactive rebase over the merge, but I'm still not thoroughly convince. Have an opinion, please let me know in the comments.

[1]: http://reinh.com/blog/2009/03/02/a-git-workflow-for-agile-teams.html
[2]: http://nvie.com/archives/323