---
layout: post
title: Heroku Fork
date: 2013-07-24 22:04:28
author: Nick Boyce
---
I've been meaning to try the [fork](https://devcenter.heroku.com/articles/fork-app) feature on Heroku for a while.

It does exactly what you expect, but that's what's so brilliant about it. It's taken be less than 2 minutes to set up a staging environment for one of our apps in the EU region. Here's what's involved:

Clone an existing app, optionally choosing a region. This will also add your add-ons to the forked app at the same payment tier so keep an eye out for this.

    heroku fork -a yourapp yourapp-staging --region eu
    
    Creating fork yourapp-staging... done
    Copying slug... done
    Adding airbrake:developer... done
    Adding memcachier:100... done
    Adding scheduler:standard... done
    Copying config vars... done
    Fork complete, view it at http://yourapp-staging.herokuapp.com/

Get the forked app's Git repo information so you can push code to it.

    heroku info -a yourapp-staging
    
    === yourapp-staging
    Addons:        memcachier:dev
                   scheduler:standard

    Git URL:       git@heroku.com:yourapp-staging.git
    Owner Email:   nick@nickboyce.com
    Region:        eu
    Stack:         cedar
    Tier:          Legacy
    Web URL:       http://yourapp-staging.herokuapp.com/

Add a new git remote so you can push to the new app.

    git remote add staging git@heroku.com:yourapp-staging.git

Push a branch to your new app.

    git push staging custom-framing:master
    
You're done!