---
layout: post
title: Data-driven UX decisions
date: 2014-05-17 15:08:52
author: Nick Boyce
---

We all make countless decisions every day when we work. What [of the hundreds of reasonable things](http://blog.samaltman.com/super-successful-companies) in my list will provide the highest value? How am I going to find the best solution for our customers? How will we know if we have even solved the problem?

At Easyart we put a lot of effort into basing our decisions on data first, and opinions second. As Jim Barksdale, former CEO of Netscape famously said:

> If we have data, let’s look at data. If all we have are opinions, let’s go with mine.

This post is about building better experiences for our customers through data-driven decisions.

## Research

### Customer research
We must understand our customers in order to solve problems for them.

#### Daily survey
Our brilliant customer service team phones a small handful of customers and asks them five questions. The answers are recorded in a Google Doc.

Though it's a small sample size but it provides useful qualitative information which helps us spot patterns in individual customer stories in a way that we could never get from an Analytics funnel or aggregate market report.

#### Market research
Periodically we conduct large-scale market research which provides us with aggregate information on our customer demographic. These are less frequent but very high sample size.

### Google Analytics, KISSmetrics, Crazy Egg and custom reporting
We use Google Analytics (from here on, GA) and KISSmetrics (from here on, KM) extensively.

#### Do and measure
Some things are not A/B testable, we don't want to clog up the testing queue, or we're confident about our hypothesis.

For every significant feature we create a GA annotation so we can do before-and-after analysis to check that everything went as expected. GA and KM provide different vantage points (*GA tells you what’s happening. KM tells you who’s doing it*), and we also use Crazy Egg for heatmap and scroll tracking.

#### Custom event tracking
We track click events on most of the elements we care about, so we can understand how users are using the site.

#### Funnels
Funnels are ways of modelling a user's journey through the key parts of your site. We keep a regular eye on these to try to identify under-performing steps that might represent problems or opportunities.

#### Custom reporting
Example: what is the average number of line items in our abandoned baskets, what is the relative performance of the main navigation vs the various search functions

## Testing

### UserTesting.com
We use [Usertesting.com](http://www.usertesting.com) to conduct remote user interviews. These allow us to observe people using the site as they follow a list of tasks we give them.

It gives us the "why" that is difficult to measure through metrics alone, and we predominantly use it to validate new UX ideas, as well as occasional competitor comparisons.

#### Watch the videos together as a team and share your findings.
It can be *extremely humbling* to you find out your brilliant idea makes no sense to the user, but it's better that these lessons are learned together.

#### Test your iterations to gain confidence
Google Ventures' Jake Knapp puts the emotional journey of user testing perfectly in [this post](http://www.gv.com/lib/the-product-design-sprint-validateday5):

> First session: “We’re geniuses!” or “We’re idiots!”
> Sessions 2–4: “Oh, this is complicated…”
> Studies 5-6: “There’s a pattern!”

By running new tests with each of our major iterations we can see quick improvement which usually results in us building enough confidence to launch (though we occasionally reject ideas that don't test well).

#### These are not real customers
It should be noted that these are not your customers, nor are they in the same frame of mind that your customers will be, so don't treat this as customer research.

### A/B testing
A/B testing can give us the *what* to the user testing's *why*, by providing a framework to validate a hypothesis.

Much has been written on the topic, and it's easy to believe it can be used to unearth hidden conversion opportunities *that will make you millions*. The truth is, not everything is suitable for A/B testing, and there is a fine art to planning tests properly.

#### Start with a strong hypothesis
Don't use a scattergun approach, this should be something you are confident about that is backed by data.

#### Ensure that the hypothesis is testable.
A good A/B testing candidate should be noticeable change, with decent traffic and an expectation for a double-digit improvement to a metric close to the area you are affecting (i.e. don't expect a change on your category page will have a measurable effect on overall conversion through your checkout).

We usually calculate the test plan using something like [experimentcalculator.com](http://www.experimentcalculator.com/)

#### Agree the success metric upfront.
Don't leave it open to interpretation, don't let ego get in the way, and *be willing to lose*. The truth can be humbling.

#### Use more than one source of data.
We use Optimizely to run the tests, but do most of our analysis through Google Analytics and KISSmetrics custom segments. This allows us to understand how users of each variation are behaving throughout their whole journey.

### Go with your gut
We don't make *every* decision using data. Sometimes it just isn't possible, particularly with creative decisions.

There is never absolute truth in numbers, and it's best to just [go with your instincts](http://www.gv.com/lib/design-instinct-vs-data) and have the confidence to push forward.
