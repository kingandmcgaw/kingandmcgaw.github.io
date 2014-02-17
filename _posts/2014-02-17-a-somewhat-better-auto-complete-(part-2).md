---
layout: post
title: A somewhat better auto-complete (part 2)
date: 2014-02-17  9:55:52
author: John Pash
---

## So how do we do this in code?
A typical auto-complete will take the input and (after sanitising of course) ask the database with a "%like%" query to find matches.

    select * from table_name where description like "%QUERY%";

This works for the most part, but doesn't do any of that fancy matching.


## Our solution
<div id="solution"></div>
[Positive zero-length lookahead assertions](http://www.regular-expressions.info/lookaround.html) of course.

But wait, *MySQL doesn't support look(ahead|behind) assertions!*, I hear you say. So we'll do it the hard way, in code.
The project I'm about to explain was done for an internal administration menu here at [Easyart](http://www.easyart.com).

![Admin menu](/assets/img/posts/admin-menu.png)

Over the years our admin has grown so large that a simple list of pages was simply too long to navigate. Even after grouping
and hiding them under dropdown menus we thought there must be a quicker way of getting to a specific page.

{% highlight php %}
<?php

// a-z only please...
$query = preg_replace("/[^a-z]/", "", strtolower(trim($_GET["q"])));

function page_description_by_character($s)
{
    return "page_description like '%{$s}%'";
}

function post_title_by_character($s)
{
    return "post_title like '%{$s}%'";
}

function page_description_regex($x)
{
    return "(?={$x}).*";
}

if ($query != "") {
    $str_split_query = implode(" and ", array_map("page_description_by_character", str_split($query)));

    $sql = "
        select
            page_id,
            page_name as url,
            page_description
        from
            admin_pages
        where
            (
                require_authorisation = 0
                or
                page_id in({$admin_user->allowed_pages})
            ) and
            show_in_menu = 1 and
            ({$str_split_query})
        order by page_description asc
    ";

    $q = exec_sql($sql, "admin_easyart");

    // MySQL doesn't support lookahead assertions so we have to do it in PHP
    $regex = "/" . implode(array_map("page_description_regex", str_split($query))) . "/i";
    
    unset($data);
    while ($q->next_record()) {
        $x = $q->aMakeResultRowArray();

        if (preg_match($regex, $x["page_description"])) {
            $x["page_id"] = (int)$x["page_id"];
            if (in_array($x["page_id"], explode(",", $admin_user->favourite_pages))) {
                $x["is_favourite"] = true;
            }
            $x["url"] = realpath(SECURE_WEB_SERVER_URL) . $x["url"];
            $data[] = $x;
        }
    }

    header('Content-type: application/json; charset=iso-8859-1');
    echo json_encode($data);
}

{% endhighlight %}
