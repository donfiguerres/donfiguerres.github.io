---
title: "Hosting a Website Using AWS S3"
description: "How to host a website using AWS S3, CloudFront with a Goddady
    domain"
date: 2022-08-04T10:23:00+08:00
#hero: images/steps-screenshot.png
menu:
  sidebar:
    name: "Hosting a Website Using AWS S3"
    identifier: hosting-website-using-aws-s3
    parent: aws
---

> **NOTE**: This post is still a work in progress.

This blog talks about how to setup a website using AWS S3 which might be
intimidating for complete beginners.
I also plan to create a tutorial/blog for complete beginners who want to setup
their own website which I should link here in the future.

## Overview

Hosting a website typically requires you to setup the following.

- Web Server - where all your files uploaded and served through the network
- Content Delivery Network (CDN) - where your static files are cached
- Certificate - for SSL
- Domain Name System (DNS) - where your domain name is registered

| Component   | What we'll use |
|-------------|----------------|
| Web Server  | S3             |
| CDN         | CloudFront     |
| Certificate | ACM            |
| DNS         | GoDaddy        |

## Step 1: Setup your S3 bucket

Create an S3 bucket in your AWS account and enable Static website hosting.
Uncheck *Block all public access* and add a bucket policy. These settings will
allow your files to be publicly accessed.

> **NOTE**: Change `Bucket-Name` into your bucket name.

```json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "PublicReadGetObject",
            "Effect": "Allow",
            "Principal": "*",
            "Action": [
                "s3:GetObject"
            ],
            "Resource": [
                "arn:aws:s3:::Bucket-Name/*"
            ]
        }
    ]
}
```

## Step 2: Setup CloudFront

Create a CloudFront distribution and use your S3 bucket as an origin.

## Step 3: Request for ACM Certificate

Request for an ACM Certificate. It is recommended to use the DNS validation
method.

### Option 1: Add DNS CNAME record to verify the ACM Certificate

Add the CNAME entry and value to the list of DNS entries in your GoDaddy domain.

> **NOTE**: It took less than 10 mins to get my domain verified.

## Step 4: Add your custom certificate to CloudFront

After receiving your certificate, add your certificate to your CloudFront
distribution.

## Step 5: Setup GoDaddy to forward your domain

Add your CloudFront distribution domain name to your GoDaddy DNS record.
