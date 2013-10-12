---
layout: post
title: On technical debt, complexity and opportunity cost
date: 2013-10-12 14:57:13
author: Nick Boyce
---
In reading [What CTOs Fear Most](https://keen.io/blog/63582764323/what-ctos-fear-most), it's clear that managing priorities is a common fear amongst technical managers.

The Easyart technical team is in the midst of redeveloping a platform that has been running for well over a decade, we are continually faced with difficult decisions about what features are worth migrating, and how they compete for resources with new features.

In our circumstance, retaining a feature is actually a new development task which is competing with every other task. Most of the existing features are there for good reason, but it's worth challeging the idea that every old feature is going to have more business value than the new features they are competing with.

Just because we can, it doesn't mean we should. Just because a feature exists, removing it doesn't necessarily make the product poorer. This point of view can be unpopular but the opportunity to shed some technical debt and rationalise our offering can make the hard work worthwhile.

Julie Zhuo, Product design director at Facebook makes the point well in her fantastic blog post [The Tax of New](https://medium.com/the-year-of-the-looking-glass/f777ec49f24a) (paraphrased here):

  > Run that line of thinking too many times and you get death by a thousand paper cuts. This is how good, simple products become quite the opposite.

  > The tax that comes with introducing any new feature into your product is high. I cannot stress this enough. Sure, maybe the new feature isn’t hard to build, maybe it only takes a couple days and a handful of people, maybe it can be shipped and delivered by next week.

  > Perhaps you will continue to develop and evolve it. Even if you don’t (maybe your plan was just to launch it and move on), the fact of its existence will inevitably create more work for you. You will get user requests and bugs about it. You will spend time thinking idly about ways to make it better. It will likely pop up in the context of your next redesign or code rearchitecture.


Another great article on the topic by Yammer's CTO, Kris Gale, [on technical debt and complexity](http://firstround.com/article/The-one-cost-engineers-and-product-managers-dont-consider):

  > For years, the two things that most frustrated me to hear from product managers were "how hard would it be..." and "can't you just..." It took me quite a while to figure out why I had such a strong, visceral reaction to these phrases. The answer seems obvious now: The work of implementing a feature initially is often a tiny fraction of the work to support that feature over the lifetime of a product, and yes, we can "just" code any logic someone dreams up. What might take two weeks right now adds a marginal cost to every engineering project we'll take on in this product in the future. In fact, I'd argue that the initial time spent implementing a feature is one of the least interesting data points to consider when weighing the cost and benefit of a feature.

And [this rant](http://insideintercom.io/there-are-no-small-changes/) argues that there is simply no such thing as a small change:

  > Agreeing to features is deceptively easy. Coding them rarely is. Maintaining them can be a nightmare. When you’re striving for quality, there are no small changes.

When you release a feature it's not the end of the job, it's just the beginning!

Thankfully none of this means we should avoid new ideas or innovation, we just need to put some process around our decisions to ensure that new features are providing value, not just technical debt.

For existing features, **study the data**. If this feature is providing real business value, it's worth retaining and developing further. If not, consider removing it.

For new features, it's important to **define success criteria upfront**. If the feature doesn't meet the measure of success you've defined, remove it. And if it does, we know the debt is worth taking on. Ideally these metrics should be published so that later down the line when someone asks "why do we have this feature", there is an answer to point to.

Adding these processes requires great discipline, but it provides a confidence that every new feature is providing real value to the company.

Update: [some discussion on Hacker News](https://news.ycombinator.com/item?id=6538833)
