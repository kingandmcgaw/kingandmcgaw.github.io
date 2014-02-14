---
layout: post
title: A (slightly) better auto-complete
date: 2013-11-12 17:37:22
author: John Pash

---

## Summary
Known by many names; the auto-complete, typeahead, search suggestion or incremental search box is an invaluable feature of any website. An example of it's use would be to find the latest news about **Lance Armstrong**. If you Google only the partial words "**lan**" and "**arm**" Google will be smart enough to fill in the blanks.

![Lance Armstrong](/assets/img/posts/lanarm.png)


### A typical auto-complete setup
A typical setup might use [Twitter's Typeahead](http://twitter.github.io/typeahead.js/) library which does an ajax call to a server which receives the partial search term and returns matching records. The results are displayed in real-time as a list of options and are updated on each keypress.


## But there's a problem
Firstly, you need to know the exact spelling of the words you are after. Many auto-complete libraries search from the beginning of words. If you miszpel your target term, you are out of luck. Good luck to sports writers wanting to find [Jhonny Peralta's](http://en.wikipedia.org/wiki/Jhonny_Peralta) batting average on your [Dominican Major League baseball blog](http://www.dominicanbaseballguy.com/).

Also, if you have many records that start with the same phrase, and your auto-complete only shows the top 10, how do you find the one that you *know* is there but is hidden at number 15?


## A better way to search
If you've ever used the [Sublime Text](http://www.sublimetext.com) editor you'll be familiar with the "search anywhere" paradigm. To find a file, normally you would go to the search box and type **filename.txt**, then hit **search**, then off it would go to hunt down your file. But with "search anywhere" you can find what you want in a fraction of the time.

For example, to search the [Rails source code](https://github.com/rails/rails) for the file "**active_record_callbacks.rb**" you could type:
  
* "**arb**" which matches "**a**ctive\_**r**ecord\_**c**allbacks.rb"
* "**reccall**" which matches "active\_**rec**ord\_**cal**lbacks.rb"
* "**arec**" which matches "**a**ctive\_**rec**ord\_callbacks.rb"

![Searching for Active Record Callback](/assets/img/posts/active-record-callback.png)

...you get the idea

Here are the rules:

* All letters must be in the name of the file (obviously)
* Letters must appear in the correct order
* Type as few or as many letters as you want

## So how do we do this in code?
The typical auto-complete setup will take the input and (after sanitising of course) ask the database with a "like" query to find matches.

    select * from table_name where description like "%QUERY%";

This works for the most part, but doesn't do that fancy middle-matching stuff where you can just throw a bunch of letters at it.


## Our solution
<div id="solution"></div>
[Positive zero-length lookahead assertions](http://www.regular-expressions.info/lookaround.html) of course!

{% highlight ruby %}
def test
  this = that
end
{% endhighlight %}

{% highlight javascript %}
function test() {
  var this = that;
}
{% endhighlight %}
