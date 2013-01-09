---
layout: post
title: Using git flow
date: 2013-01-09 15:46:43
author: Steve Rydz
---

For the past couple of weeks I've been using a tool called [Git Flow](https://github.com/nvie/gitflow). In it's own words, git flow is *A collection of Git extensions to provide high-level repository operations for Vincent Driessen's [branching model](http://nvie.com/git-model).*

If you're already familiar with Git on the command line then getting up and running with git flow will take you no time at all.

### Installation

The full installation instructions [can be found here](https://github.com/nvie/gitflow/wiki/Installation) but for the purposes of this article I am going to assume you are on a Mac and using homebrew.

You can use homebrew to install git flow:

		$ brew install git-flow

That's all it takes.

### Initialising a project

To use git flow, you will need to already have a git project set up. So, to get started, just navigate to your project (in Terminal) and type the following:

		$ git flow init

It will then ask you a few questions regarding what to name your various branches. Unless you have good reason, I would stick to the defaults.

### Going with the flow

So now you have initialised git flow within your project, you want to get going.

The assumption here is that your master branch is always deployable and your develop branch is where you would make small changes that will be release fairly quickly.

The feature I use most is *feature* branches. Essentially a branch called feature/<feature-name> is created and when complete, merged into your develop branch. To start a new feature branch just type:

		$ git flow feature start <feature-name>

Obviously feature name will be whatever you want to call your new feature. You can then start working on your feature and commit as you normally would. To set up a remote branch so others can collaborate just use the publish command:

		$ git flow feature publish <feature-name>

Once you are ready to merge your new feature, just use the finish command:

		$ git flow feature finish <feature-name>

This will merge your feature into your develop branch and delete your local branch too. If you want/need to delete the remote branch then just type:

		$ git push origin :feature/<feature-name>

### More resources

Hopefully this article has convinced you that using git flow is worthwhile and got you intrigued enough to find out more.

Some more git flow resources:

* [Why aren't you using git flow](http://jeffkreeftmeijer.com/2010/why-arent-you-using-git-flow/)
* [Getting started with git flow](http://yakiloo.com/getting-started-git-flow/)
* [Oh the path with git flow](http://vimeo.com/37408017)
* [How to use a scalable git branching model called gitflow](http://buildamodule.com/video/change-management-and-version-control-deploying-releases-features-and-fixes-with-git-how-to-use-a-scalable-git-branching-model-called-gitflow)
* [A short introduction to git flow](http://vimeo.com/16018419)