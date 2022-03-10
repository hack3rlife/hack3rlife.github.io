---
title: "Configure Cloudfront for Secure Delivery of Static Websites Around the World"
position: 5
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

# Overview

# AWS Certificate Manager.
1. Login to [AWS Console](console.aws.amazon.com)
1. Open [AWS Certificate Manager](https://us-east-2.console.aws.amazon.com/acm/home)
1. Click on <b>Request</b> button.
1. On Request Certificate Page, under Certificate Type section, choose <b>Request a public certificate</b>.
[![Hosted Zones](https://i.ibb.co/tQ9fRKj/Request-Certificate-0.png)](https://i.ibb.co/tQ9fRKj/Request-Certificate-0.png)
1. On Request public certiciate page, under Domain Names section, type your domain name in <b>Fully qualified domain name</b> (e.g.: hack3rlife.website).
1. Choose <b>DNS Validation</b> under Select validation method section.
[![Hosted Zones](https://i.ibb.co/T1NSh2L/Request-Certificate-1.png)](https://i.ibb.co/T1NSh2L/Request-Certificate-1.png)
1. Click on <b>Request</b> button. 
[![Hosted Zones](https://i.ibb.co/MZNws6X/Request-Certificate-2.png)](https://i.ibb.co/MZNws6X/Request-Certificate-2.png)
1. Click on <b>Create records in Route 53</b> button.  
[![Hosted Zones](https://i.ibb.co/tZ6ZSx9/Request-Certificate-3.png)](https://i.ibb.co/tZ6ZSx9/Request-Certificate-3.png)
1. Select your doman name for the list and click on <b>Create Records</b> button.  This automatically adds a DNS record to your domain that allows Amazon Certificate Manager to validate you are the owner of the domain.
[![Hosted Zones](https://i.ibb.co/w7hfcG0/Request-Certificate-4.png)](https://i.ibb.co/w7hfcG0/Request-Certificate-4.png)

# Update Amazon CloudFront Distribution Configuration
1. Go to [Amazon  CloudFront](https://console.aws.amazon.com/cloudfront/) console. 
1. Select your Amazon CloudFront Distribution.
1. Under General section, click <b>Edit</b> button.
[![Hosted Zones](https://i.ibb.co/StX3frD/Update-Distribution-0.png)](https://i.ibb.co/StX3frD/Update-Distribution-0.png)
1. Type your domain name in <b>Alternate domain (CNAME) - optiional</b> (e.g.: `hack3rlife.website`)
1. In <b>Custom SSL Certificate</b> select the certificate created in Amazon Certificate Manager.
[![Hosted Zones](https://i.ibb.co/vJmPLP9/Update-Distribution-1.png)](https://i.ibb.co/vJmPLP9/Update-Distribution-1.png)