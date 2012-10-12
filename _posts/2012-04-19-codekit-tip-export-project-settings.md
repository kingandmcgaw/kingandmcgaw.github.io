---
layout: post
title: "Codekit tip: Export project settings"
date: 19th April 2012
author: Steve Rydz
---

A few weeks ago I wrote about [getting to know CodeKit](/2012/03/23/getting-to-know-codekit). As a team, we have been using this tool solidly since then and it is now hard to imagine not working without it.

We did have a couple of issues with it though. The first was that everytime we updated the app, we had to set up our project again. This has been fixed in a recent release.

The other issue was that when working as a team, we had to ensure that we all had the exact same set-up. CodeKit is very intelligent and recognised what we were trying to acheive most of the time but we still found ourselves having to update output directories etc.

As it turns out, there was one simple solution to both of these problems. It is possible to export a config file for each project with it’s settings. This file lives in the root directory of your project and every time you drag a project into CodeKit, it looks for this file automatically.

<img src="/assets/img/posts/codekit-2.png" alt="Codekit">

To export the configuration file, simply highlight the project you are currently working on, right click on it, hover over the ‘Project settings’ menu, then click ‘Export project configuration file’. CodeKit will then place that file in the root directory of your project. That’s all there is to it.

This approach has worked really well for us and taken the burden of having to constantly ensure we are all doing the same thing away from us. The other great thing about this is that we now have this config file in our GIT repository.

All we have to do if we change the way our project is set up or introduce something new is to export another file and because we are using GIT, we will all get the latest file when we pull down the latest code.

**Note:** According to the CodeKit website, the free, BETA version of the app expires tomorrow (20th April, 2012), and I have heard rumours that it will be on sale via the app store for around $20. This app is more than worth that amount and if this is the case, I will certainly be purchasing a license first thing.