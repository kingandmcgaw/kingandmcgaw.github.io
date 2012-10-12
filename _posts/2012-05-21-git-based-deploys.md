---
layout: post
title: Git-based deploys
date: 21st May 2012
author: Nick Boyce
---

Recently we've switched from FTP to git to deploy changes to our live sites. Here's what our workflow looks like for functional changes (content amends use steps1,2,5,7,8):

<img src="/assets/img/posts/git.jpg" alt="Git-based deploys">

1. Make changes on VMs on develop branch
1. Commit and push develop branch to Github
1. Pull develop branch to staging server
1. Review changes
1. Merge develop into master
1. Run Selenium tests
1. Push master to Github
1. Pull master into live server

By using a Git-centric workflow, it's easier to guarantee that each application is running the same code, and we have the added safety of being able to roll back to previous versions.

Pulling changes onto live websites with millions of daily visitors makes me a little nervous, so I'll usually use *git fetch* rather than *git pull*, like so:

    $ git fetch

Pulls the remote master branch into a branch in the local repository called origin/master.

    $ git diff --numstat master origin/master

Reports the affected files between master and the origin/master branch we pulled in the previous step.

  $ git merge master origin/master

Merges the origin/master branch into master.