---
layout: post
title: Full Frontal Tooling
date: 2012-11-07 20:25:51
author: Steve Rydz
---

I've just got back from the [Full Frontal Tooling Workshops](http://2012.full-frontal.org/#tooling) in Brighton, so I thought I'd best write about my experience whilst it's still fresh in my mind.

### The set up

There were six different workshops in total, with [Remy Sharp](http://remysharp.com), [Rebecca Murphey](http://rmurphey.com) and [Jake Archibald](http://jakearchibald.co.uk/) each leading two sessions. They were structured so participants could attend *any* four of the workshops throughout the day. The topics were:

* **Modularizing your JavaScript with RequireJS** &mdash; Rebecca Murphey
* **Writing Testable JavaScript** &mdash; Rebecca Murphey
* **Massive git** &mdash; Jake Archibald
* **It's your Sass on the line** &mdash; Jake Archibald
* **Debugging** &mdash; Remy Sharp
* **Build Process** &mdash; Remy Sharp

### What to choose?

I chose the require.js, testable JavaScript, debugging and build process workshops. I didn't opt for the git workshop as I use it daily and am relatively comfortable with it and the same goes for Sass (although we currently use LESS at Easyart). Whilst I'm sure they were great workshops, I felt I would benefit a lot more from the others, especially as they addressed topics that I have become very interested in lately.

### Modularizing your JavaScript with RequireJS

We started with an existing project, which had several script tags linking to various JavaScript files such as jQuery, Backbone, Underscore and more. Rebecca then showed us how to use [require.js](http://requirejs.org/) and the [AMD format](https://github.com/amdjs/amdjs-api/wiki/AMD) to manage our dependencies and modules, and then going on to build the project with a simple command.

This got me thinking about the way our JavaScript is structured, and whilst it has certainly seen improvement over the past six months or so, it could be taken a stage further by introducing require.js into our process.

### Writing Testable JavaScript

We have been focusing on [Test-driven development](http://en.wikipedia.org/wiki/Test-driven_development) quite a lot lately and have also identified that we need to be doing unit tests on our JavaScript so this topic was particularly relevant to me.

Rebecca introduced us to [QUnit](http://docs.jquery.com/Qunit) and explained the thought-process behind unit testing and writing testable JavaScript.

When carrying out unit tests, we are essentially asking the following question:

> Given this input, do I get this output?

&mdash; Rebecca Murphey

This sounds simple, and really it is. The main thing to get your head around is writing JavaScript that is actually testable. Rebecca showed us some *typical* jQuery code, which was distinctly lacking in functions or output, and explained how it was very difficult to test, and went on to explain how to write JavaScript that actually returns something so we can test it.

> Things don't do things &mdash; Things announce things

&mdash; Rebecca Murphey

The process of writing good tests should be to make them fail first, and then write the necessary code to make them pass. Well written tests not only ensure that your code is actually working, they help you to write better code.

One point that stood out to me in this workshop was not to get too hung up on testing edge cases. Make your tests as thorough as they need to be and then if an edge case does occur, write the test, then fix the problem.

Later, we were briefly introduced to [Mocha](http://visionmedia.github.com/mocha/), a more advanced testing framework, and also shown how to integrate testing with [grunt.js](http://gruntjs.com).

### Debugging

Being a developer, I'm no stranger to the Chrome developer tools but I've never really used them to their full potential. 

During this workshop, Remy introduced us to the concept of step debugging and setting breakpoints. I had come across breakpoints before but wasn't really sure how I could use them to debug code so I found this really helpful.

Something Remy said, which I have heard quite a lot, is that if you are using alerts for debugging you should stop right now. <code>console.log</code> is your friend.

After a run through of the various tabs in the Chrome developer tools, Remy talked to us about mobile debugging.

Debugging code in mobile browsers can be a nightmare, but Remy showed us something called [weinre](http://people.apache.org/~pmuellr/weinre/docs/latest/), which basically listens to your ip address and binds itself to it, allowing you to open the developer tools on your machine and debug in your mobile browser.

One thing that was stressed was the importance of testing on real devices. Emulators are fine for getting a quick overview but if you are doing any mobile specific work, get real phones.

### Build Process

This workshop was based around a tool called [Grunt](http://gruntjs.com), which is, in its own words, a task-based command line build tool for JavaScript projects.

Grunt is very powerful and can take care of a lot of otherwise mundane tasks for you such as:

* Concatenating files
* Generating project scaffolding
* Linting your code
* Minifying your code
* Running unit tests
* Starting a static web server

These are just the built-in tasks. Grunt is still very new but despite this, there are already over 200 plugins available.

This got me thinking about our build process and how it could be streamlined using this tool. We currently compile, concatenate and minify our Less files using [CodeKit](http://incident57.com/codekit/), the same goes for our JavaScript which we also run through JSHint. This works for us, but can sometimes feel cumbersome.

The possibilities with Grunt are endless and I also feel like it would give us more control over our projects so it is definitely something I will investigate adding to our process.

### Conclusion

I really felt like I got a lot out of these workshops today. It was a lot of information to take in but the key points all came across. I really liked the format and 90 minutes seems to be about the perfect length for workshop sessions of this kind. 

I don't know if Remy is planning to do something similar next year but if he does I hope I will be lucky enough to attend once more.