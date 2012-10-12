# The Easyart Developers Blog

## Set-up

### Install Jekyll

    $ sudo gem install jekyll

### Install RDiscount (required for markdown)

    $ sudo gem install rdiscount

### Clone repo

    $ git clone git@github.com:easyart/developers.easyart.git

## Write a new post

Navigate to the project root and use the following command to generate a new post (replacing "post-title" with the title of your post):

    $ rake newpost["post-title"]

## Run the site locally

To run the site on your computer, navigate to the root and run the following command:

    $ jekyll --auto --server

You will then be able to view the site at localhost:4000

## Deployment

Coming soon&hellip;