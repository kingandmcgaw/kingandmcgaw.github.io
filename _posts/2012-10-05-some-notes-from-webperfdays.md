---
layout: post
title: Some notes from WebPerfDays
date: 5th October 2012
author: Nick Boyce
---

I'm just back from [WebPerfDays](http://webperfdays.org/) at Facebook's [London engineering offices](http://www.facebook.com/facebooklondon) in Covent Garden. It was a really great day out, with some great presenters.

A few notes&hellip;

* [Joshua Bixby](http://www.webperformancetoday.com/) is a really good presenter and I'll be following his blog.
* Not all performace stats apply to all companies. There were several examples cited of how reducing page load time had either no discernable effect, or even a negative impact (though they were very specific cases).
* "Mortal companies" have different problems to the Googles, Facebooks and Amazons of the world.
* Using a CDN doesn't guarantee those assets are delivered to the user faster. Our measurements would suggest otherwise, but a second look at the data would be wise.
* 97% of mobile response time is on the front end!
* I like the concept of a "poverty line" in performance. i.e. if a metric is below a certain threshold it's "poor".
* A significant percentage of mobile users prefer the full site rather than a mobile version.
* Simply cleaning up code and doing all the things you already know you should be doing will get you 80% of the way to where you need to get to with front-end code.
* We should check out [writegoodcode.com](http://www.writegoodcode.com/).
* After you optimise your front-end code, you have to be be vigilant about maitaining the gains you have made.
* Other people probably have more difficult performance problems to solve than us. Seatwave have to cope for massive (60x) request peaks in requests in a matter of seconds (i.e. when their TVC is aired in the middle of X-Factor or a new concert goes on sale).
* We should take a close look on the performance of our third party dependencies. They are generally recognised as evil when it comes to web performance.
* Lonely Planet have a really great DevOps culture in their company (see their (dev blog)[http://devops.lonelyplanet.com/]) where metrics are king and web performance is recognised as a priority throughout the whole organisation. * They have gone some way to replacing “HiPPO” (Highest Paid Person’s Opinion) with real data. 
* Webpagetest.org is a tool that a lot of web performance experts seem to refer to.
* Facebook have problems that are extremely unique, and fascinating from an observer's standpoint, but intimidatingly complex from a developer's. Sławek Biel did a really interesting presentation about how Facebook optimises its data access.
* Overall, it's just reminded me that we need to continue to focus on performance as part of what we do.

Update: Some of the presentations are [now available online](http://www.seriticonsulting.com/blog/2012/10/8/webperfdays-summary-and-slides.html).