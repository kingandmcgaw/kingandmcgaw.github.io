---
layout: post
title: Using Selenium and Rspec for behaviour testing
date: 1st May 2012
author: Nick Boyce
---

We've been doing some restructuring here at Easyart, in order to set up a more Git-centric workflow for deployments. We wanted to make sure that we had some tests which would help us spot any problems while we made the transition.

I'm relatively comfortable with Rspec, so it was a natural starting point. But given that the sites themselves aren't built in Ruby, I'm using Rspec to power Selenium Webdriver.

Here's a sample test:

<script src="https://gist.github.com/2566740.js"> </script>

The Selenium::WebDriver object makes writing these tests pretty simple. These are the main methods we use:

* find_element and find_elements
* get (or navigate.to, which I think are identical)
* title

That's pretty much it! These are the methods in the Selenium::WebDriver::Element object we are making the most use of:

* text
* click
* send_keys

Here's an example which makes use of these:

<script src="https://gist.github.com/2566849.js"> </script>

One thing that took some getting used to was using the Selenium::WebDriver::Wait object. When you do a click, you have to tell Selenium you want to wait for a certain condition to be true before moving on to the next live of code. 

In this example, I'm waiting until the H1 tag contains the word "cart":

<script src="https://gist.github.com/2567891.js"> </script>

I'm used Rspec for unit and request specs, but it's advantageous to use a visible browser for this type of testing, as sometimes you can spot things with your eye that your tests won't. Then you write the test to catch it.