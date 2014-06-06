---
layout: post
title: iOS event bubbling
date: 2014-06-06 10:41:44
author: Steve Rydz
---

The great thing about being a web developer is that you get to learn new things all the time. This week, I learned something really simple, but it had a big impact:

*iOS doesn't respect event bubbling without a cursor style!*

This amazed me. We have what we like to call popovers in various places on our main site, similar to [these](http://getbootstrap.com/javascript/#popovers). Ours differ, in that we have a fullscreen, transparent div positioned behind them so the user can close them by clicking anywhere on the page. I discovered this wasn't working in iOS.

The code looks something like this:

{% highlight javascript %}
$(document).on("click", ".popover-overlay", function () {
	$(".popover-overlay").remove();
});
{% endhighlight %}

There didn't seem to be anything wrong with the code and it worked everywhere else. We use similar looking code on other areas of the site and they were working in iOS. I was very confused at this point.

The difference between this specific example and the other places event bubbling is used was that the element we are targeting is not a link. It turns out that unless the element you are targeting has a cursor style applied, iOS won't respect event bubbling.

After all that head scratching, the fix turned out to be:

{% highlight css %}
.popover-overlay {
	cursor: pointer;
}
{% endhighlight %}

I couldn't believe this. Especially as there is no visible cursor on iOS anyway!