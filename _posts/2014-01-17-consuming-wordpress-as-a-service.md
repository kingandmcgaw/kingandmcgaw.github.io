---
layout: post
title: Consuming Wordpress as a service
date: 2014-01-17 16:04:10
author: "Steve Fuller"
---

Our Wordpress blog is a useful tool for publishing marketing information and one we wanted to keep in our new site as it provides useful information for customers as well as helping to keep the content of the site fresh.

We didn't necessarily want all the features of Wordpress so beloved of developers the world over, just the content posts, assets and a means of querying the different categories we'd set up.

We used the [JSON_API](http://wordpress.org/plugins/json-api/) plugin to do the job. It installs into a wordpress instance and exposes a number of REST methods allowing our rails controller to fetch and parse the blog content efficiently (caching it for performance). The plugin doesn't include any authentication options but if you only enable the get methods it's no more public than a hosted Wordpress site.

There were a few small customizations to Wordpress we added - essentially to disable frontend access so that the content only appears in the context of our [main website](http://www.easyart.com/trends). Splitting the content management off into a separate service like this both fits with the SOA structure of Easyart and means our editors can add and edit content without affecting anything that might be happening on the rest of the platform.
