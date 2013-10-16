---
layout: post
title: Setting Up Google Tag Manager with Optimizely
date: 2013-10-16 14:07:47
author: John Pash
---

### Summary
We've recently moved over to using [Google Tag Manager](www.google.co.uk/tagmanager‎) (GTM) on the redesign of [Worldgallery](www.worldgallery.co.uk). The promise of being able to *"update your website tags...without bugging the IT folks."* was too hard to pass up. The reality of GTM, however, has proven to be something all together different.

We also use [Optimizely](https://www.optimizely.com/) quite heavily on the new site. And the easy integration with Google Analytics(GA) via [Custom Variables](https://developers.google.com/analytics/devguides/collection/gajs/gaTrackingCustomVariables) mean that we can easily segment the Optimizely visitors by buckets. For instance, we can run a report that gives us "Ecommerce value of all visitors who saw Version A of the checkout page" or "Time on page for visitors who saw Version B of a certain landing page". This greatly enhances the default reporting from Optimizely.

### The Problem
Now that Google Tag Manager is responsible for loading all javascript on the page, we need to be sure that they get executed in the correct order. And that order is 1) Optimizely followed by 2) Google Analytics

By default, GTM does what it does as and when it sees fit. So we can't be sure that the tags will fire as needed. However the fix for this particular problem [has already been solved](http://www.verticalnerve.com/blog/detail?id=278).

In a nutshell:

- Load the Optimizely code in a GTM **[Custom HTML Tag](https://support.google.com/tagmanager/answer/2574372#CustomHTML)**.
- Then set a dataLayer variable in that tag which says "OK - Ready to go"
- That then triggers the GA pageview to fire. Simple!

But that wasn't enough to make it work...

Yes, we could fire the GA pageview at the right time - after Optimizely has done it's thing. But for some reason the Custom Variables still weren't being sent along with the request.

### The Solution
Fast forward about 30 hours of head-scratching and a large handful of experiments. When finally the missing piece of the puzzle was found.

There is a [poorly documented](https://support.google.com/tagmanager/answer/2574372#TrackerName) feature of GTM for the **Tracker Name** setting. Reading this would lead one to believe that all this setting does is allow you to *"name the tracker object yourself"*.

What isn't mentioned is that by turning on this setting (which can be found under **Advanced Settings** for the **Page View** tag) you effectively make the tracker name public. This is your UA-XXXXXX-X number. Without this information Optimizely is not able to set the Custom Variable correctly.

### Conclusion
If you use **Google Tag Manager** along with **Optimizely** and want to take advantage of **Google Analytics** *Custom Variable* segmentation - pause for breath - then you need to:

1. Tick the box next **Tracker Name** under **Advanced Settings** (but don't fill anything in the text box!)
2. Follow [these instructions](http://www.verticalnerve.com/blog/detail?id=278) to ensure the correct load order of scripts
3. GOTO PUB
