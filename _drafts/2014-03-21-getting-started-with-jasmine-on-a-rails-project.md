---
layout: post
title: Getting started with Jasmine on a rails project
date: 2014-03-21 15:08:52
author: Steve Rydz
---

We're big fans of [TDD](http://www.agiledata.org/essays/tdd.html) here at Easyart. So far this has only applied to our Ruby code, but with JavaScript increasingly becoming a bigger part of our technology stack, we needed to start testing that too.

### Choosing the right tool
We chose [Jasmine](http://jasmine.github.io/2.0/introduction.html) as our testing framework, partly because of its similarity to RSPEC, and also because its really easy to get started with.

You can get started with Jasmine fairly quickly. Their [standalone distribution](https://github.com/pivotal/jasmine/tree/master/dist) has everything you need to get up and running. Opening the included `SpecRunner.html` will run the example tests and show you the results. From here you can swap out the example files with your own.

![the Jasmine specrunner](/assets/img/posts/jasmine-specrunner.png)

### Getting up and running on rails
Once we settled on Jasmine, we needed a way to integrate it into our current workflow, as we don't want to be running tests manually all the time.

Luckily, there is an official [Jasmine gem](https://github.com/pivotal/jasmine-gem). To add this to your project add the following to your gemfile:

{% highlight ruby %}
group: development, :test do
	gem "jasmine"
end
{% endhighlight %}

To setup the file structure that the gem expects for your tests, run the following command from your CLI, which will set up all the necessary files and directory structure to begin testing your code:

{% highlight ruby %}
rails g jasmine:install
{% endhighlight %}

### Running the tests
There are two ways you can run your Jasmine tests. The first is to run the following rake task:

{% highlight ruby %}
rake jasmine
{% endhighlight %}

This will fire up a web server, accessible at `localhost:8888` where you will see an HTML document displaying the results of your tests.

You can also run the tests in continuous integration mode from the command line, which will show you the results in the terminal:

{% highlight ruby %}
rake jasmine:ci
{% endhighlight %}

![the Jasmine CLI specrunner](/assets/img/posts/jasmine-CLI-specrunner.png)

### Integrating into your build process
Depending on your environment, you may have to add the `ci` rake task to your deployment process, but we currently use [CircleCI](http://circleci.com) which picked it up automatically, which means our test run every time we deploy, and if they don't pass, the build will fail.

### Writing the tests
As I mentioned before, Jasmine is easy to get started with, as long as you are reasonably comfortable with JavaScript, but if like me, you're new to writing tests it can be hard to figure out where to start.

The key is to write code that is actually testable. The simplest way to do that is to ensure your code returns something. I attended a testing workshop a little over a year ago with [Rebecca Murphey](http://rmurphey.com), and she described this as:

> "Things don't do things - things announce things"

She also advised to have the following question in mind when writing tests:

> "Given this input, do I get this output?"

For more on testable JavaScript, I recommend starting with [Rebecca's A List Apart article](http://alistapart.com/article/writing-testable-javascript).

### Going forwards
So far we don't have as much JavaScript code coverage as we would like, but  with a little discipline we'll eventually get to a place where we can be confident that our code is always working.