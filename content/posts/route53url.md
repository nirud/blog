---
title: "Redirect with Amazon Route 53 DNS Service"
date: 2018-12-23T19:25:26+01:00
draft: true
featuredImg: ""
tags: 
  - aws
  - amazon
  - dns 
---

While creating my blog I stumbled accross the problem to redirect users from my domains to my blog. 
I wanted to redirect [www.nilsrudolph.de](https://www.nilsrudolph.de) and [nilsrudolph.de](https://nilsrudolph.de) to [blog.nilsrudolph.de](https://blog.nilsrudolph.de).

Some DNS services allow such a feature via an URL record but this is not an official record and not supported by Route 53.
But by using the Amazon S3 service you can archive the same result.
Create a S3 bucket, choose some name and keep all default settings. After you created the S3 bucket go to the bucket and open properties and choose "Static website hosting". There you can configure a "Redirect request".

![Static Website Hosting](/img/posts/static-website-hosting.png)

Now you can add an A record for your domain in Route 53. Set "Alias" to "yes" and choose your new S3 bucket. 

Note: You have to wait a some time after you create the S3 Bucket to choose it as alias in Route 53.

