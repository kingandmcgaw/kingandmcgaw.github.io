---
layout: post
title: A unified coding style
date: 12th April 2012
author: Steve Rydz
---

Something we have been working on recently is finding a unified coding style that we are all comfortable with. The benefits of this are that any one of us can pick up a project and run with it as we are already familiar with the way the project has been set up.

Another aim of ours when authoring code is to be as efficient as possible, not just in terms of file size but in terms of maintainability also.

One tool we have been using to help us acheive this is LESS. Combining LESS with our own coding conventions, each of us can quickly find what we are looking for in our CSS and can also make changes quickly, knowing that what we are doing will be maintainable.

An example would be nesting. LESS allows you to nest selectors like so:

    #header {
      overflow: hidden;

      h1 {
        font-size: 3em;
      }
    }

As someone who doesn’t have a background in programming, I did find this initially confusing, but it soon begins to make sense and once you start working this way you will probably never want to go back.

This code will output as follows:

    #header {
      overflow: hidden;
    }

    #header h1 {
      font-size: 3em;
    }

Something else you will notice in the above snippet is that there is a blank line before the descendent selector, an no blank lines after the closing brakets. This is something we agreed upon as a standard because it makes code more readable.

It doesn’t matter what your coding conventions are, as long as they make sense to you and your team, but using them will increase productivity considerably and are worth the investment in time it takes to establish them.

Another thing that is worth doing, and again, something we are working on, is drafting a [CSS styleguide](https://github.com/styleguide/css). This is something that you can add to over time as and when you add new tools and methodologies into your process, such as we have, working with LESS and CodeKit.

The key thing to remember is that whatever you come up with, it needs to be something that your team can all get on board with, as the aim is to increase productivity and make things easier to maintain.