—
layout: post
title: The simplest way to prioritise your backlog
date: 4th September 2015
author: Nick Boyce
—
The King & McGaw development team uses a scrum-like process to manage the features we build. It looks a little bit like this:

<img src="https://cdn-images-1.medium.com/max/1046/1*VVv-xcYwVQ90r6xZ8vcS0Q.png">

We’ve found this process to be super helpful for building things, but figuring out what to build is often more difficult.

### “Everything is important”

* Difficult to prioritise business as usual (BAU) tasks against features when we have only one team
* Difficult to prioritise platform development (strategic impact) with features (customer impact)
* No procedure for researching the expected impact of a feature
* Difficult for development team to see what is coming down the pipeline

## How we prioritise features now
Anyone in the company is allowed to add to the backlog, and at least once a fortnight we prioritise the features using this simple ranking system:

<img src="https://cdn-images-1.medium.com/max/761/1*GM6floXz5cZdmW1YmaB4zA.png">

* **Impact** — expected creation or protection of revenue or other strategic objective
* **Ease** — the cost in man-hours to get the job done

The result is then multiplied by two and given a final percentage score (well, out of 98). Any task which is expected to have maximum ease (typically BAU tasks, less than 2 hours) can jump the queue and be scheduled for development at the discretion of the team. That’s it! Or is it?

## What if we don’t have enough information to rank the feature?

### If we can’t estimate the impact

* Data analysis! Extract the information you need from historical sales data, Analytics, server logs or whatever is appropriate
Clarify objectives with stakeholders, especially if it’s an internal requirement
* Model the expected outcome (“lifting this metric by x % will have this effect”)
* In any of these scenarios we will add a book icon (📚) until we have enough information to rank the feature.

### If we can’t estimate the ease
* There are multiple ways to solve the problem, and perhaps a simple implementation will have less of an impact than a complex one so it also affects impact. Pick one, and rank based on that.
* The problem has not been defined well enough for the developers to estimate.
* In any of these scenarios we will have a small workshop to uncover the challenges and propose the most likely outcome.

## It’s not perfect
Ultimately it provides us a good structure without being overbearing. It also means we need to be disciplined. If there is something we really believe in, but it doesn’t have a ranking which will allow it to be developed, perhaps we need to look at ways to make it easier, or to have a higher impact.
