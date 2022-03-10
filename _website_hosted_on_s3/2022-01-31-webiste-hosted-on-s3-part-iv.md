---
title: "Configuring a static website using a custom domain with Route 53"
position: 4
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
1. A registered domain or get ready to register one.

# Overview
In this post, I'll use my registered domain (`hack3rlife.website`) and configure Amazon Route 53 to route traffic from `hack3rlife.website` to Amazon CloudFront.

#  Register a custom domain
1. Go to to prefereded registrar and buy a domain or do it 
    * I used [Namecheap](https://www.namecheap.com/) to regiser my domain. I think one of the chepeast and perfect for this tutorial.  

# Amazon Route 53 Configuration
1. Login to [AWS Console](console.aws.amazon.com)
1. Open the [Route 53](https://console.aws.amazon.com/route53/) console

## Create a Hosted Zone
1. Click on <b>Hosted Zones</b> 
[![Hosted Zones](https://i.ibb.co/hFpp12z/Create-Hosted-Zone-0.png)](https://i.ibb.co/hFpp12z/Create-Hosted-Zone-0.png)
1. Clikc on <b>Create Hosted Zone</b>

1. Under Hosted zone configuration 
    * Domain Name: {YOUR_CUSTOM_DOMAIN} (e.g.: `hackerlife.website`)
    [![Hosted Zones](https://i.ibb.co/6YSkm1w/Create-Hosted-Zone-3.png)](https://i.ibb.co/6YSkm1w/Create-Hosted-Zone-3.png)
 1. Clikc on <b>Create Hosted Zone</b>   
    Amazon Route 53 will create two records
    * An NS record. (You'll need to copy and paste these values in your registrar)
    * A SOA record.
    [![Hosted Zones](https://i.ibb.co/VLGcYRj/Create-Hosted-Zone-5.png)](https://i.ibb.co/VLGcYRj/Create-Hosted-Zone-5.png)

1. In your registrar domain management, add the 4 name servers that Amazon Route 54 created.
[![Hosted Zones](https://i.ibb.co/gZbDrhn/Create-Hosted-Zone-7.png)](https://i.ibb.co/gZbDrhn/Create-Hosted-Zone-7.png)
1.  Add an alias records for your domain. 
    * Create a Record
    * Choose Simple routing, and choose Next.
    * Choose Define simple record.
    * In Record name, accept the default value (should be the name of your hosted zone and your domain)
    * In Value/Route traffic to, choose Alias to CloudFront Distribution and add your CloudFront Distribution Name (e.g.: `https://d3e1f693x86xgv.cloudfront.net`)
    [![Hosted Zones](https://i.ibb.co/Zdg5NkM/Create-Hosted-Zone-6.png)](https://i.ibb.co/Zdg5NkM/Create-Hosted-Zone-6.png)
    
1. Browse to your domain name (`http://hack3rlife.website/`)
[![Hosted Zones](https://i.ibb.co/Q8Jrhb2/Create-Hosted-Zone-8.png)](https://i.ibb.co/Q8Jrhb2/Create-Hosted-Zone-8.png)

No worries, that error is expected.  There is one step we need to perform.  We need to configure CloudFront to handle requestes coming from your domain (e.g.: `hack3rlife.website`). To fix this, we need to create a Custom SSL certificate which validate that request coming from our domain are valid and can be routed to our cloudfrond distribution.



