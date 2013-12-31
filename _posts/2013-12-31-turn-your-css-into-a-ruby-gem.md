---
layout: post
title: Turn your CSS into a ruby gem
date: 2013-12-31 11:26:25
author: "Steve Rydz"
---

In our never-ending mission to make our codebase more maintainable, we decided to package up our shared CSS into a gem so we can use it on all of our projects easily, without having to worry about things going out of sync.

This seemed daunting to me, as I'd never done anything like this before, but after some reading and googling, I found it wasn't actually that complicated. Here's how I did it:

## What you'll need
* Ensure rubygems is up to date by running `gem update --system` from your terminal
* Install **bundler** by running `gem install bundler`
* A [github](http://github.com) repo for the gem
* An account on [Rubygems](http://rubygems.org)

## Creating the gem
**Note:** I've called my gem *craven*, so wherever you see this, you should replace it with the name of your gem.

You can use bundler to create the scaffolding for your gem. All you have to do is run:

		bundle gem craven

Believe it or not, this is almost good-to-go, but we need to do a small amount of config first.

Open the file `craven/lib/craven.rb` and edit it so it looks like this:

		require "craven/version"

		module Craven
			class Engine < Rails::Engine
			end
		end

Now open the file `craven/craven.gemspec` and fill out any sections containing `TODO:`. I also set the homepage to my github repo:

		spec.homepage = "http://github.com/easyart/craven

## Adding your assets
Now you can add your assets to the gem. Assuming your assets are intended to be used as a library, you should use the `vendor` directory structure, so all your stylesheets are included in  `craven/vendor/assets/stylesheets/craven/`.

## Bumping the version number
Now you are almost ready to publish your gem, but each time you do, you will need to bump up the version of your gem, otherwise it will fail. You can do this in `craven/lib/craven/version.rb`.

## Publishing the gem
Now for the exciting part - you're about to publish your first ruby gem. To do this, just run:

		bundle exec rake publish

This will publish the gem and push your changed to github. The first time you do this you will be prompted to fill out some credentials. From then on, all you will have to do is run the above command to publish changes to your gem.
