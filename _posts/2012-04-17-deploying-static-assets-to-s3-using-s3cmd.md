---
layout: post
title: Deploying static assets to S3 using s3cmd
date: 17th April 2012
author: Nick Boyce
---

I've been looking at ways to deploy our static assets to S3 as part of our Git workflow.

I want to be able to push to the master branch of a remote repo and have the changes deployed to S3, with predefined HTTP headers. Much like I'm used to pushing to Heroku with git push heroku master.

There are probably plenty of ways to do it - mounting S3 through Fuse, running Webdav servers, using Capistrano etc - but I found them too overkill for our needs.

So I've ended up writing a simple deploy script which lives at the root of the repo which uses [s3cmd](http://s3tools.org/s3cmd) to sync between the local file system and our S3 bucket. It's a snap to set up, and the result is a command that looks like this:

<script src="https://gist.github.com/2404535.js"> </script>

I store this file in the repo, so that each of us developers can execute it by just calling ./deploy.sh. As this process is outside of the Git workflow, I have to exclude the .git directory. Conveniently, s3cmd's format for excluding files is the same as Git's so you can pass in a .gitignore if you're using one.

It's not a true Git deploy (though it could be called via a [Git Hook](http://progit.org/book/ch7-3.html)), but still a pretty neat solution.