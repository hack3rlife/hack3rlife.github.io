---
title: "Hosting a static website using Amazon S3"
position: 2
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
1. At least one index.html and optionally one error.html static web pages.  I'll use my static web site I created in the [previous](./2022-01-31-webiste-hosted-on-s3-part_i) post of this serie.
1. An AWS Account.  
    * Sing in [here](https://signin.aws.amazon.com/)
    * Create a brand new (free) account [here](https://aws.amazon.com/free/)

# Overview
When we configure a bucket as a static website, we must enable static website hosting, configure an index document, and confiugre permissions. In this post, I'll show you how to create a bucket, enable statick web hosting and configure required permission visualize a static website hosted in Amazon.

# Amazon S3 Bucket Configuration
1. Sign in to the [AWS Management Console](console.aws.amazon.com). 
[![Create Bucket](https://i.ibb.co/jfSpgGR/Create-Bucket-0.png)](https://i.ibb.co/jfSpgGR/Create-Bucket-0.png)

1. Open [Amazon S3 Console](https://s3.console.aws.amazon.com/s3/home) service.
[![Create Bucket](https://i.ibb.co/R0f021L/Create-Bucket-1.png)](https://i.ibb.co/R0f021L/Create-Bucket-1.png)

## Create a S3 bucket for your root domain
Based on [Amazon documentation](https://docs.aws.amazon.com/AmazonS3/latest/userguide/creating-bucket.html) the bucket name must be a DNS-compliant name which means:
* Be unique across all of Amazon S3.
* Be between 3 and 63 characters long.
* Not contain uppercase characters.
* Start with a lowercase letter or number.

**NOTE** After you create the bucket, you cannot change its name. 

For more inforation, visiti [Bucket naming rules](https://docs.aws.amazon.com/AmazonS3/latest/userguide/bucketnamingrules.html)
1. Choose <b>Create Bucket</b>.
1. Bucket Name: `hack3rlife.website`. {YOUR_BUCKET_NAME}
1. AWS Region: `us-east-2`. {YOUR_AWS_REGION}
[![Create Bucket](https://i.ibb.co/9cWZh8x/Create-Bucket-2.png)](https://i.ibb.co/9cWZh8x/Create-Bucket-2.png)

1. In Block Public Access settings for this bucket: Disable Block all public access.
    [![Create Bucket](https://i.ibb.co/SB05wQF/Create-Bucket-3.png)](https://i.ibb.co/SB05wQF/Create-Bucket-3.png)

1. Click on <b>Create Bucket</b>

## Enabling website hosting
1. In the Buckets list, choose the bucket you just created.
 [![Create Bucket](https://i.ibb.co/hVpx6GD/Create-Bucket-4.png)](https://i.ibb.co/hVpx6GD/Create-Bucket-4.png)
1. Choose Properties.
1. Under Static website hosting, choose Edit.
1. Enable static website hosting.
1. In Index document, type index.html.
[![Create Bucket](https://i.ibb.co/FVs9PHG/Create-Bucket-6.png)](https://i.ibb.co/FVs9PHG/Create-Bucket-6.png)
1. Click on <b>Save Changes</b> button.

## Attach a bucket policy
1. Under Buckets List, choose the bucket you created in the previous steps
1. Choose Permissions.
1. Under Bucket Policy, choose Edit.
1. We need to grant public read access, so copy and paste the the following one in the Bucket Policy Editor.
```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "PublicReadGetObject",
            "Effect": "Allow",
            "Principal": "*",
            "Action": "s3:GetObject",
            "Resource": "arn:aws:s3:::{YOUR_BUCKET_NAME}/*"
        }
    ]
}
```
1. Click on <b>Save Changes</b> button.

## Updload your website
1. Go to bucket's Object tab.
1. Click on the <b>Upload</b> button.
1. Drag & Drop your files and folders. 
1. Click on <b>Upload</b> button.
1. Test it: `http://{YOUR_BUCKET_NAME}.s3-website.{YOUR_AWS_REGION}.amazonaws.com/` (`http://aws-blog.hack3rlife.website.s3-website.us-east-2.amazonaws.com/`)