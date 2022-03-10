---
title: "Creating a Jekyll Site"
position: 1
date: 2021-11-03T08:00:00-07:00
categories:
  - blog
tags:
  - aws-s3
  - route53
  - cloudfront
  - jekyll
  - github
  - github-actions
---

### Before you start
Here is what you need for this post.
1. IDE Editor like [Visual Studio Code](https://code.visualstudio.com/download) but you can even use Windows Notepad or [Notepad++](https://notepad-plus-plus.org/downloads/)
1. IIS. You need to have installed and configured IIS on your development machine.

# Overview
In this post, I'll show you how to create, build and configure Windows environment for Jekyll.  In case you don't know it, [Jekyll](https://jekyllrb.com/) is a static site generator and I'll use it to create a sample static website which I'll host later on Amazon S3.

# Jekyll installation
1. Install all [prerequisites](https://jekyllrb.com/docs/installation/).
1. Install Jekyll 
    * Open a command prompt and execute the following command `gem install jekyll bundler`
1. Create a new Jekyll site 
    * Go to the directory where you want to create the site (`C:\inetpub\wwwroot`)
    * Execute the following command `jekyll new S3Website`    
1. Build the site 
    * Go to the new directory `cd S3Website`
    * Execute the following command `bundle exec jekyll build`

Our website is ready.  It's time to configure IIS so we can be able to visualize it.

# IIS Configuration 
1. Open IIS Manager.
1. Add a new WebSite.
    * SiteName: {OUR_WEBSITE_NAME} (`S3Website`}
    * Physical Path: {YOUR_WEBSITE_PATH}\_site  (`C:\inetpub\wwwroot\S3Website\_site`)
    * Port: {HTTP _PORT} (`8082`)
1. Browse to `http://localhost:8082/`

# Update our new website
1. Go to your {YOUR_WEBSITE_PATH} (`C:\inetpub\wwwroot\S3Website`)
1. If you are using Visual Studio Code, just do a rick click and select <b>Open with Code</b> to open the whole folder. Otherwise, just open `_config.yml` in Notepad or any other editor.
    * Update title.
    * Update email
    * Update descripton
    * Update twitter_username
    * Update github_username
1. Once you finish your changes, save it and execute the followin execute the following command `bundle exec jekyll build`.
1. Test it: 
    * Browse to `http://localhost:8082/` or just update your explorer window.
