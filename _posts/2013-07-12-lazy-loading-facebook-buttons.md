---
layout: post
title: Lazy loading Facebook buttons
date: 2013-07-12 16:13:45
author: Steve Rydz
---

We recently did the WordPress work for the [Art Everywhere](http://arteverywhere.org.uk/) project, and one of the requirements of the project was to include a Facebook like button for each artwork on the [Choose Artworks](http://arteverywhere.org.uk/artworks/) page.

That page has around 100 artworks on it so immediately I heard alarm bells, until I remembered the [Socialite plugin](http://socialitejs.com/). This allows you to lazy-loading the Facebook buttons.

No matter what, we didn't want all of those Facebook buttons to load at the same time, even if the rest of the page had already loaded, so we decided we would load them in on hover.

Initially we struggled to get this working how we wanted, as all the buttons would load when you hovered over any of the buttons. Finally [Nick](http://easyart.github.io/authors/nick-boyce/) found the solution:

	$(".artwork-info").hover(function () {
		Socialite.load(this);
	});

It turns out, all we had to do was pass `this` to the `Socialite.load` function. So, if ever you find yourself having to implement similar functionality, you know what to do.