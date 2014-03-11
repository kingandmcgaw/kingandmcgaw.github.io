---
layout: post
title: Improving our development cycle
date: 2014-03-11 14:28:29
author: Nick Boyce
---
I've been struggling to solve a problem for some time now. The agile (with a lower-case "a") [approach](/2013/04/16/easyart-flavoured-agile/) we use for software development and the long-term roadmaps we have as a business have always been too disconnected, but I never quite knew how to connect them.

Recently, inspired by a deeper understanding of the [lean approaches](/2014/02/16/lean-ux-at-easyart/), I think I've finally connected them together in these five steps. It's still an emerging process, but I'm hopeful it will solve a number of problems.

### Keep an inventory of hypotheses
We all have ideas for ways to improve the site. Some of them are bound to make a positive difference, others will make the site worse, and most will have no measurable effect at all.

We keep a spreadsheet of these ideas, documented as hypotheses (if I do x, y will happen), along with as much additional information as we have. This ideas backlog becomes our ammunition to improve the site. Importantly, these are not added to Basecamp, where the tasks live until they have been prioritised.

### Establish themes
In order to prioritise the ideas backlog, I work with other managers to decide on a theme for each month. To establish the theme we might look at under-performing parts of the conversion funnel, goals in other parts of the business, tech roadmap etc.

Sometimes the theme might be very specific (increase percentage of framed products sold), or more generic (increase AOV or improve funnel conversion for search, product, cart, order complete).

Rallying the team around a focussed goal helps us dive deeper into interconnected ideas. We spend 60% of our development time working on tasks related to the theme, while the other 40% is reserved for fixing bugs, cost of doing business tasks, documentation, research etc.

### Prioritise hypotheses around themes
Once the theme is established, we hold a workshop to prioritise the hypotheses from the backlog in the ways most likely to improve the target KPI.

These competing ideas will vary wildly in difficulty and will probably contradict each another. Using experiment mapping and PIE ranking we can prioritise these based on value.

### Create tasks from prioritised hypotheses
Once priorities are established, tasks are added to the "Next up" or "Backlog" lists in Basecamp, along with the corresponding hypothesis. Depending on our level of confidence in the task, we may use a combination of data analysis, user testing and competitor analysis to research the best solution.

Tasks move through a Kanban-esque process through "In Progress" and "QA" through its lifecycle, collecting more and more information as it goes.

### Validate hypothesis
Once in "QA", a combination of user testing and split testing will be used to validate or invalidate our hypothesis.

Minor variations will take a long time to reach statistical confidence, so we only split test meaningful changes. We always agree on the measure of success upfront, but also cross-check side-effects with Analytics segments.

Once a conclusion is reached, the task is marked as complete, links to the task/discussion/tests added to the spreadsheet before it's moved to a "completed tests" sheet, and annotations added to Analytics for before-and-after analysis.

With each test, we increase our shared understanding of what our customers want, which in turn generates high quality ideas for future testing.
