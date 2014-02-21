---
layout: post
title: A somewhat better auto-complete (part 2)
date: 2014-02-17  9:55:52
author: John Pash
---

This is part 2 of a post which tries to explain a method of enhancing an auto-complete search box to act in a similar way to the Google search box.
[&raquo; Read part one here &laquo;](/2013/11/12/a-somewhat-better-autocomplete/)

## A solution
Something that would work perfectly for this style of query would be to use a regular expression query with a [lookahead assertion](http://www.regular-expressions.info/lookaround.html).

But wait, *MySQL doesn't support look(ahead|behind) assertions!*, I hear you say. That's ok, we'll do it the hard way, in code.

## The query
First we need to mangle the input into a query that will get us most of the way using plain old sql. For example, if the user enters the string **pcr** (perhaps looking for the **p**rint **c**ategory **r**eport), we want to end up with the following:

{% highlight sql %}
select * from admin_pages where (
    page_description like '%p%' and 
    page_description like '%c%' and 
    page_description like '%r%' )
{% endhighlight %}

This will return all pages that have **every** one of those letters in the description in alphabetical order.

* /admin/**p**rint_**c**atego**r**ies.php
* /admin/**p**rodu**c**t_sales_**r**eport.php
* /admin/su**p**plier_sto**c**ked_item_**r**eport.php

But there's a problem. The ordering of letters matters. We only want pages that contain a **p** followed by 0 or more letters, then a **c** followed by 0 or more letters, followed by an **r**. No matter, this will at least give us something to start with. It's better than stuffing the entire database table into memory for searching.

The code that constructs this query is below (I've removed any security/sanitisation code to avoid cluttering up the example.):

{% highlight php %}
<?php
function page_desc_sql($s) {
    return "page_description like '%{$s}%'";
}

// a-z only please...
$query = preg_replace("/[^a-z]/", "", strtolower($_GET["q"]));

// build query
$s = implode(" and ", array_map("page_desc_sql", str_split($query)));

$sql = "
    select
        page_id,
        page_name,
        page_description
    from
        admin_pages
    where
        ({$s})
    order by page_description asc
";
?>
{% endhighlight %}

So now we have a list of pages ready to process. Let's create that lookahead expression.

{% highlight php %}
<?php
function page_regex($x) {
    return "(?={$x}).*";
}
$regex = "/" . implode(array_map("page_regex", str_split($query))) . "/i";
?>
{% endhighlight %}

This sets $regex to the string:  
**/(?=p).\*(?=c).\*(?=r).*/i**

The final piece of the puzzle is to take the results and pass them through this regex, only returning the ones that match. Then output some json for the auto-complete to use.

{% highlight php %}
<?php
    while ($q->next_record()) {
        $x = $q->get_row();

        if (preg_match($regex, $x["page_description"])) {
            $x["page_id"] = (int)$x["page_id"]; // Cast integer for json
            $x["url"] = realpath(SECURE_WEB_SERVER_URL) . $x["url"];
            $data[] = $x;
        }
    }

    header('Content-type: application/json; charset=iso-8859-1');
    echo json_encode($data);
}
?>
{% endhighlight %}
