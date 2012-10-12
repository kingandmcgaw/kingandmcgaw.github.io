---
layout: post
title: History state and the back button
date: 11th April 2012
author: Nick Boyce
---

I've been playing around with the HTML5 history API today, in order to make certain parts of our new product page bookmarkable. Here's what we're aiming for:

1. On page1.html, the user clicks an a tag which has a href value of page2.html
1. Instead of refreshing the page with the contents of framing.html, a panel in the page slides across to reveal the contents of page2.html in the current page
1. The URL changes to page2.html

This is relatively easy to achieve by intercepting these links, and replacing them with Javascript behavior and using the HTML5 History API to push a new URL into the address bar. So, as an example, the following code will find every a on the page and instead of navigating to the href, just push the state into the address bar.

<script src="https://gist.github.com/2359314.js"> </script>

So we can quite easily intercept links to page2.html (either based on their href attribute or a CSS class), push the href into the address bar and load the content into the current page in some fancy-pants way.

But say you want the back button to navigate the user from page2.html back to page1.html. This won't work, because unless you tell it to do otherwise, the back button will change the address, but do nothing else.

This is where popstate comes in. Using popstate we can listen for changes in the address, and act upon them accordingly. So my code ended up looking something like this:

<script src="https://gist.github.com/2359401.js"> </script>

It's also possible to pass objects and titles through to pushstate, but I won't go into that for now as it's not yet well supported by browsers. Simply finding out the address of the page was good enough to solve the immediate problem.

Resources:

[http://diveintohtml5.info/history.html](http://diveintohtml5.info/history.html)
[https://developer.mozilla.org/en/DOM/Manipulating_the_browser_history](https://developer.mozilla.org/en/DOM/Manipulating_the_browser_history)