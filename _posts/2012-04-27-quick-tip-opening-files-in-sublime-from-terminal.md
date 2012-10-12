---
layout: post
title: "Quick tip: Opening files in Sublime from Terminal"
date: 27th April 2012
author: Steve Rydz
---

Sublime Text 2 has been my text editor of choice for almost a year now but as I find myself working from the command line more and more these days, I thought I’d share a quick tip I picked up from Nick, opening files from the command line.

### Getting set up

To begin with, we need to ensure that the bin directory is specified in our path. Just paste the following into Terminal:

    $ echo "export PATH=~/bin:$PATH" >> ~/.profile

Next up, we need to create the subl command. To do that just paste the following into Terminal:

    $ ln -s "/Applications/Sublime Text 2.app/Contents/SharedSupport/bin/subl" ~/bin/subl

To make sure this is working, just type subl into Terminal and press enter. If you’ve followed the steps above then that should open up Sublime.

### Using the command

We’ve already seen how the subl command can be used to open Sublime itself, however it can also be used to open files and directorys, among other things.

This command opens a directory called mySite:

    $ subl ~/Documents/mySite

This command opens a file from the above directory called index.html:

    $ subl ~/Documents/mySite/index.html

### Taking it further

This only scratches the surface of what you can do with this type of command. To see other actions available, try typing subl --help into Terminal and pressing enter. This will give you a list of ways to use this command.

**Note:** This post is pretty much lifted from a post I wrote on my own blog last night:

[http://steverydz.com/2012/04/27/sublime-text-2-opening-files-and-folders-from-the-command-line/](http://steverydz.com/2012/04/27/sublime-text-2-opening-files-and-folders-from-the-command-line/)