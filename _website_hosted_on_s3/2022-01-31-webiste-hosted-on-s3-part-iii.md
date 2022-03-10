---
title: "Improving performance of an Amazon S3 website with Amazon CloudFront"
position: 3
layout: single
author_profile: true
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
1. S3 Bucket with static hosting enabled

# Overview
After hosting a static website on Amazon S3, I'll show you how to speed up it with Amazon CloudFront

# Amazon CloudFront Configuration
1. Login to [AWS Console](console.aws.amazon.com)
1. Go to [Amazon  CloudFront](https://console.aws.amazon.com/cloudfront/) service. 
[![Create Distribution](https://i.ibb.co/WKt2Ryh/Create-Distribution-1.png)](https://i.ibb.co/WKt2Ryh/Create-Distribution-1.png)

## Create a distribution
1. Clikc on <b>Create Distribution</b> button.
1. For Origin Domain, type the Amazon S3 website endpoint for your bucket. (e.g.: `aws-blog.hack3rlife.website.s3.us-east-2.amazonaws.com`)
1. Name: It will auto-populate with the value selected in Origin Domain
[![Create Distribution](https://i.ibb.co/4FMKjDZ/Create-Distribution-2.png)](https://i.ibb.co/4FMKjDZ/Create-Distribution-2.png)
1. For Viewer protocol policy, pick **Redirect HTTP to HTTPS**
[![Create Distribution](https://i.ibb.co/rFftvnm/Create-Distribution-3.png)](https://i.ibb.co/rFftvnm/Create-Distribution-3.png)
1. Click on <b>Create Distribution</b> button.
1. Test it. I might take a couple of minutes before the distribution is ready. Check the Status column in the distribution console to verify the current status. Once the distribution is deployed, copy the Distribution Domain Name and paste it in your browser. (e.g.: `http://d3e1f693x86xgv.cloudfront.net/`)