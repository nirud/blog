---
title: "Redirect with Amazon Route 53 DNS Service"
date: 2018-12-23T19:25:26+01:00
featuredImg: ""
tags: 
  - aws
  - amazon
  - dns 
---

While creating my blog I stumbled across the problem to redirect users from my domains to my blog. 
I wanted to redirect [www.nilsrudolph.de](http://www.nilsrudolph.de) and [nilsrudolph.de](http://nilsrudolph.de) to [blog.nilsrudolph.de](https://blog.nilsrudolph.de).

Some DNS services allow such a feature via an URL record but this is not an official record and not supported by Amazons Route 53.

But by using the Amazon S3 in combination with the Route 53 service you can archive the same result.

You need to create a S3 bucket with web-hosting enabled which does the redirect and then create a DNS A record which points to the S3 bucket.

First create a S3 bucket, the name has to be the same as the domain you want to redirect from, e.g. [www.nilsrudolph.de](http://www.nilsrudolph.de) and keep all default settings. After you created the S3 bucket go to the bucket and open properties and choose "Static website hosting". There you can configure a "Redirect request".

![Static Website Hosting](/img/posts/static-web-hosting.png)

Now you can add an A record for your domain in Route 53. Set "Alias" to "yes" and choose your new S3 bucket as "Alias Target". 

Note: You have to wait a some time after you create the S3 Bucket to choose it as alias in Route 53.

