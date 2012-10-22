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

## Run the site locally

To run the site on your computer, navigate to the root and run the following command:

    $ jekyll --auto --server

You will then be able to view the site at localhost:4000

## Deployment

To deploy the site, just commit the new post and push to the master branch. The changes should be relected at: [http://easyart.github.com](http://easyart.github.com)