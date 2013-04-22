---
layout: post
title: Transitioning to Bourbon
date: 2013-04-22 11:01:48
author: Steve Rydz
---

With the project we're currently working on, I was tasked with taking the lead on the front-end side of things. Previously we used Bootstrap, with our styles applied on top, but this was no longer a good fit for a number of reasons:

1. Large amounts of unused CSS
2. Components had to be overwritten to fit our designs
3. The grid system wasn't particularly flexible

My gut feel was that we need our own framework, but before we went down that road, I took a look at some other options.

At one point we tried Foundation, mainly because the grid system seemed to be quite clever, but there were a number of reasons why that also didn't work:

1. Once again, large amounts of unused CSS
2. Changing font sizes altered the grid system
3. Browser support doesn't reach back as far as we need it to

I decided to piece together our own framework, but to save time I wanted a reliable and flexible grid system, oh, and it had to be twelve columns. 

After trying out numerous pre-built grid systems and finding none of them worked as we wanted, I was ready to give up and build it myself, until my colleague Nick discovered [Neat](http://neat.bourbon.io).

Neat is the grid system that accompanies [Bourbon](http://bourbon.io), a solid collection of Sass mixins and utilities. After trying it out for an hour or so, I decided this was what we needed.

The great thing about using bourbon and neat is that only the styles we are actually using will be included in our compiled CSS, and we can also easily use our own classes keeping both our HTML and CSS as clean as possible from presentational class names.

I was now ready to piece together our framework. I already had some styles which were a mix of our own global styles, some bootstrap components (alerts, wells, labels etc), and a few other bits and pieces. These are now kept in their own [github repo](http://github.com/easyart/craven), and will be included as a git submodule going forward.

Here is a broad outline of how we now structure our CSS:

* **Bourbon**: Up-to-date CSS3 mixins
* **Neat**: Stable and flexible grid system
* **Config**: Variables to customize aspects of each site
* **Craven**: Collection of styles inc. normalize, bootstrap components and global styles
* **Site specific**: Any styles specific to each site

So far we've found this to be a maintainable way to structure our CSS, and we're hoping once we port it across all of our sites it will continue to be so.

