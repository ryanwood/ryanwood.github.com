---
layout: post
title: "Deploying Refinery On Heroku"
date: 2009-09-18 09:50
comments: true
tags: [refinery heroku git deployment]
---
Recently, I have been exploring [Refinery](http://refinerycms.com/), a relatively new Rails-based CMS. So far I've been very impressed. One of the sites I been implementing in Refinery will be deployed to [Heroku](http://heroku.com/) which has [some constraints](http://docs.heroku.com/constraints) which cause the out-of-the-box version of Refinery to fail. Here's how to get it working if you're interested.

*Updated [9/19/2009]: After corresponding with [David](http://www.d-jones.com/) at [Resolve Digital](http://resolvedigital.co.nz/), I added step 2 and corrected a couple of file references. Thanks for the input David.*

## Prerequiste

You will to have or create an new account with [Amazon S3](http://aws.amazonaws.com/s3) or another third party storage solution supported by [attachment\_fu](http://github.com/technoweenie/attachment_fu).

## Step 1: Config your buckets

You will need to update your `config/amazon_s3.yml` file to include you bucket name, access key, and secret key.

    development:
      bucket_name: myapp-development
      access_key_id: XXXX
      secret_access_key: XXXX
      distribution_domain: XXXX.cloudfront.net

    ... same for test and production

*Note: You will need to create this bucket before you can use it. I used [CyberDuck](http://cyberduck.ch/) on the mac to connect S3 and create the initial buckets. Check out the bottom of  [this post](http://www.hongkiat.com/blog/amazon-s3-the-beginners-guide/) for some alternatives.*

## Step 2: Override the files we will be updating so they don't conflict when Refinery is updated

This is the "approved" approach to take if you are changing elements of Refinery. Simply override the particular file in `app` directory and your Rails app will load it instead of the Refinery equivalent in the plugins directory. Let's override the models we need to update...

    mkdir -p app/models
    cp vendor/plugins/images/app/models/image.rb app/models
    cp vendor/plugins/inquiries/app/models/inquiry.rb app/models
    cp vendor/plugins/news/app/models/news_item.rb app/models
    cp vendor/plugins/pages/app/models/page.rb app/models
    cp vendor/plugins/resources/app/models/resource.rb app/models

## Step 3: Override Images and Resources to use S3

In `app/models/image.rb`, you will need change the options for has\_attachment:

    # From this...
    has_attachment :content_type => :image, 
                   :storage => :file_system,
                   :path_prefix => 'public/images/system',
                   :processor => 'Rmagick', 
                   ...

    # To this...
    has_attachment :content_type => :image,
                   :storage => :s3,
                   :processor => 'Rmagick',
                   ...
 
And in `app/models/resource.rb`:

    # From this...
    has_attachment :storage => :file_system,
           :size => 0.kilobytes..50.megabytes,
           :path_prefix => 'public/system/resources'
           
    # To this
    has_attachment :storage => :s3
           :size => 0.kilobytes..50.megabytes #,

This should now send uploads to S3.

## Step 4: Update search index location

We now need to update the options hash for [acts\_as\_indexed](http://douglasfshearer.com/blog/rails-plugin-acts_as_indexed) in each of the models that we overwrote in step 1. You will need to add the following key pair to the hash:

    :index_file => [RAILS_ROOT,'tmp','index']

For example, in `app/models/image.rb`

    acts_as_indexed :fields => [:title]
    # becomes
    acts_as_indexed :fields => [:title], :index_file => [RAILS_ROOT,'tmp','index']

Make sure you find each instance where acts\_as\_indexed is used. It would be nice if you could just update a global setting that would override the default, but as of this writing, you have to do it on each model.

## Step 5: Create a .gems file

Heroku requires a `.gems` file for it to install the required gems on their servers. Create `.gems` in the root directory with the following content.

    unicode
    # Add any other gems you require here
    
## Step 6: Deploy

Now comes the easy part...

    git push heroku master
    
Tada ... you're live on Heroku.
