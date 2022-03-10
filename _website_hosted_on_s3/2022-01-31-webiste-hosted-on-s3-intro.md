---
title: "Hosting a static website using Amazon S3"
layout: single
author_profile: false
position: 0
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

# Overview
In this post, I'll show you how to create a static website using Jekyll, commit changes in a Github repository and automatically deploy it to AWS S3 with Github Actions.

<b>Amazon Route 53</b> is a serice which a allows to register domains and to define where you want to route internet traffic for your domain.

Once we have our sie hosted on AWS S3, I'll show you how to speed up our website with Amazon CloudFront and configure a custom domain with Route53.

# Architecture
![Architecture](https://i.ibb.co/M7ntR2n/hosting-website-on-s3-architecture.png)

# Before you begin
<b>Amazon S3</b> is the service which allows us create buckets, upload files (static website), configure permissions so it can be publicly accessed, and then configure the buckets for website hosting.

# Rerences
1. [Jekyll](https://jekyllrb.com/)
1. [Hosting a static website using Amazon S3](https://docs.aws.amazon.com/AmazonS3/latest/userguide/WebsiteHosting.html)
1. [Configuring a static website on Amazon S3](https://docs.aws.amazon.com/AmazonS3/latest/userguide/HostingWebsiteOnS3Setup.html)
1. [Configuring a static website using a custom domain registered with Route 53](https://docs.aws.amazon.com/AmazonS3/latest/userguide/website-hosting-custom-domain-walkthrough.html)
1. [S3 Bucket action doesn't apply to any resources](https://stackoverflow.com/questions/44228422/s3-bucket-action-doesnt-apply-to-any-resources)