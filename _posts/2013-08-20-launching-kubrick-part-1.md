---
layout: post
title: Launching Kubrick, part 1
date: 2013-08-20 12:45:14
author: Nick Boyce
---
After a period of beta testing, user testing and painful analysis, last week we migrated [WorldGallery.co.uk](http://www.worldgallery.co.uk) to Kubrick, the new platform we've been working on in the London office. Kubrick's primary objectives are textbook e-commerce, but the technology and processes are a bit more interesting (which I will write about later)

### Improving conversion rate
When you have a product catalogue as extensive as WorldGallery, it's a challenge to help users find the product they want to find. I think this is particularly true of art products which are often difficult to categories.

The primary focus has been a new category structure, and adding the capability for users to navigate directly to artwork, artist or category pages via a new search auto-suggest feature. The result is a more curated user experience.

* Key tech: Rails, Sinatra, ElasticSearch, JSON

### Improving AOV
We have a massive range of frames and a brilliant team of master framers, and frankly we need to do a better job of getting our customers interested in frames. To do this, we've integrated framing directly into the main product page and made it near-instantaneous to navigate between various types of unframed, canvas or framed products.

* Key tech: Backbone, JSON

### Increase traffic
We've vastly simplified the structure of the site (focussing on artworks, categories, artists and artworks), resulting in a more easy-to-understand structure, more crawlable pages, one "true" URL for each page (rather than rewrites which can result in multiple URLs for a single entity).

* Key tech: Rails, Rack::Rewrite

We also had some **secondary goals** in this development, which are mainly to do with our internal goals within the team.

* Make the site mobile-friendly for the 25% (and rising) of users that access our sites on tablets or mobile
* Improve engagement (measured in time on site, number of page views and return visits)
* Improved monitoring
* Automated testing

We're already seeing some positive results and look forward to migrating some of our other sites over.
