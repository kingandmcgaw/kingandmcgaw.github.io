---
layout: post
title: Adding dependencies to your ruby gem
date: 2014-01-03  9:43:45
author: "Steve Rydz"
---
A couple of days ago I wrote about [turning your CSS into a ruby gem](http://easyart.github.io/2013/12/31/turn-your-css-into-a-ruby-gem/). Since then my colleague [John](http://easyart.github.io/authors/john-pash/) suggested that I add [Bourbon](http://bourbon.io) and [Neat](http://neat.bourbon.io) as dependencies, as the SCSS included in the gem will not work without them.

So, once again I was faced with a new challenge - and once again it turned out to be fairly simple in the end.

I won't go into details about the different kinds of dependencies you can use in a gem, [the rubygems guide](http://guides.rubygems.org/patterns/#declaring_dependencies) does a better job of that than I would, but the process is the same either way.

In your `<gem name>.gemspec` file, you just need to add the following:

		spec.add_dependency "bourbon", ">= 3.1.4"
		spec.add_dependency "neat", ">= 1.3.0"

Obviously the name and version number of the gems you include here will be whatever you are using on your project.

The next, and final step is to go to `lib/<gem name>.rb` and require your dependencies at the top of the file, underneath your `<gem name>/version` require statement:

		require "bourbon"
		require "neat"

And that's it. Next time you (or someone else) uses your gem, the dependencies will be installed without having to include them separately.
