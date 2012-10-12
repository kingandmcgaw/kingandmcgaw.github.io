---
layout: post
title: Testing Rails JSON APIs with RSpec
date: 10th April 2012
author: Nick Boyce
---

I've spent some time in the last couple of weeks taking the learnings from an early API prototype, and starting a new Rails application from scratch, complete with RSpec tests. Here are some notes on some of our tools and methodologies.

### Model specs

We're overriding the as_json method in our models and we're using [json_spec](https://github.com/collectiveidea/json_spec) to test the documents have the right structure.

<script src="https://gist.github.com/2349770.js"> </script>

### Request specs

We have hundreds of lines of [request specs](https://www.relishapp.com/rspec/rspec-rails/docs/request-specs/request-spec), and no controller specs. Here is a simple example:

<script src="https://gist.github.com/2349801.js"> </script>

Because we're getting an actual HTTP payload back (in the response variable) we can inspect whatever part of it that's relevant to us. We know the structure of the responses should come back in a known format because we're testing the to_json method in the class specs. So it's just a matter of using JSON.parse on the response.body and testing it as a native Ruby object.

Of course, this means that we are trusting JSON.parse to behave reliably but that's an assumption worth making. If we were really pedantic, we could check that each object in the response array matches the expected structure:

<script src="https://gist.github.com/2349803.js"> </script>

Though I'm not sure that's actually testing anything meaningful.

Another great advantage is that it makes refactoring simple. As far as the specs are concerned, a request to is the same whether the heavy lifting is done in the model or the controller. This really helped me recently when I moved a bunch of logic from the controller to the model as I could let the specs tell me which parts starting misbehaving.

Update: [An interesting post by DHH about over-testing.](http://37signals.com/svn/posts/3159-testing-like-the-tsa)