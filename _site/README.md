# The Easyart Developers Blog

## Set-up

### Install Jekyll

    $ sudo gem install jekyll

### Install RDiscount (required for markdown)

    $ sudo gem install rdiscount

### Clone repo

    $ git clone git@github.com:easyart/easyart.github.com

## Write a new post

Navigate to the project root and use the following command to generate a new post (replacing "post-title" with the title of your post):

    $ rake newpost["post-title"]

Or if you are on ZSH:

    $ rake 'newpost[post-title]'

## Write a draft post

Navigate to the project root and use the following command to generate a new draft post (replacing "post-title" with the title of your post):

    $ rake newdraft["post-title"]

Or if you are on ZSH:

    $rake 'newdraft[post-title]'

## Run the site locally

To run the site on your computer, navigate to the root and run the following command:

    $ jekyll server --watch

You will then be able to view the site at localhost:4000

## Run the site and display drafts

To run the site locally and view drafts run the following command from the root of the project:

    $jekyll server --watch --drafts

## Deployment

To deploy the site, just commit the new post and push to the master branch. The changes should be reflected at: [http://easyart.github.com](http://easyart.github.com)
