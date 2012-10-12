---
layout: post
title: Cheating isn't always a bad thing
date: 17th April 2012
author: John Pash
---

I read a thought-provoking comment today on [High Scalability](http://highscalability.com/blog/2012/3/26/7-years-of-youtube-scalability-lessons-in-30-minutes.html) that got me thinking. It appeared in a post which attempted to sum up "[7 Years of YouTube Scalability Lessons in 30 Minutes](http://highscalability.com/blog/2012/3/26/7-years-of-youtube-scalability-lessons-in-30-minutes.html)". It shows a neat little trick that you can use to make it appear to the user that your site is faster than it really is. Read on&hellip;

### Approximate Correctness - Cheat a Little

> A real world example. If you write a comment and someone loads the page at the same time, they might not get it for 300-400ms, the user who is reading won’t care. The writer of the comment will care, so you make sure the user who wrote the comment will see it. So you cheat a little bit. Your system doesn’t have to have globally consistent transactions. That would be super expensive and overkill. Not every comment is a financial transaction. So know when you can cheat.

So basically you would update the page DOM in real-time, but send the actual comment post operation behind the scenes. It can take as long as it needs to complete. But in the meantime the commenter is happy to have such a quick experience. It's a win-win!

High Scalability is a blog that exposes the architecture of some very well-known and highly trafficked  websites. The posts are often written by the developers of those systems. So if you've ever wondered how [Twitter stores 250,000,000 tweets a day](http://highscalability.com/blog/2011/12/19/how-twitter-stores-250-million-tweets-a-day-using-mysql.html) using MySql (no NoSql here), then H.S. is the blog for you.