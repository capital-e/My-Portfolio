<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Host a Website on Amazon S3

**Project Link:** [View Project](http://learn.nextwork.org/projects/aws-host-a-website-on-s3)

**Author:** Jonathan Nutsugah  
**Email:** nutsugahjonathan@gmail.com

---

![Image](http://learn.nextwork.org/amused_pink_zesty_alpaca/uploads/aws-host-a-website-on-s3_5d4474f9)

---

## Introducing Today's Project!

In this project, I will demonstrate how to create an Amazon S3 bucket and use it to host a static website. I'm doing this project to learn how to store and serve files like pictures and HTML pages directly from S3.

### Tools and concepts

I learned how to use S3, EC2, IAM, VPC endpoints, and bucket policies to securely host a static website on AWS.

### Project reflection

30 Minutes.

---

## How I Set Up an S3 Bucket

Creating an S3 bucket took me barely 2 minutes.

The Region I picked for my S3 bucket was US-east-1 because it is the default AWS Region, widely supported, often has lower latency and pricing, and works well for general testing and learning purposes.

S3 bucket names are globally unique! This means that no two buckets anywhere in the world, even across different AWS accounts, can have the same name at the same time.

![Image](http://learn.nextwork.org/amused_pink_zesty_alpaca/uploads/aws-host-a-website-on-s3_ba6d42ad)

---

## Upload Website Files to S3

### index.html and image assets

I uploaded two files to my S3 bucket - they were the HTML file and the folder containing my images.

The HTML file is the structure of my website, while the image folder contains the visuals that the HTML file displays. I need both because the HTML file references those images to show them on the website properly.

![Image](http://learn.nextwork.org/amused_pink_zesty_alpaca/uploads/aws-host-a-website-on-s3_a265af88)

---

## Static Website Hosting on S3

Website hosting means storing website files (like HTML, images, and CSS) on a server so that people can access your site through the internet. When someone visits your website link, the host delivers those files to their browser.

I enabled website hosting by going to my S3 bucket’s settings, selecting the “Properties” tab, then turning on “Static website hosting.” I specified the index document (like index.html) so AWS knows which file to load when someone visits my site.

An Access Control List (ACL) manages who can access your S3 bucket and what they can do. I enabled ACLs to control permissions more precisely.

![Image](http://learn.nextwork.org/amused_pink_zesty_alpaca/uploads/aws-host-a-website-on-s3_c22c54c0)

---

## Bucket Endpoints

A bucket website endpoint URL is the web address that lets people access your S3 bucket’s static website over the internet. It points to the hosted site files you set up in your bucket for website hosting.

When I visited the bucket website endpoint URL before setting the permissions, I saw an error message because the HTML and image files were still private. This stopped the website from showing properly since the files needed to be publicly accessed.

![Image](http://learn.nextwork.org/amused_pink_zesty_alpaca/uploads/aws-host-a-website-on-s3_22ce4daf)

---

## Success!

I fixed the 403 error by making my S3 files public using ACLs. Once they had public read access, my website loaded successfully.

![Image](http://learn.nextwork.org/amused_pink_zesty_alpaca/uploads/aws-host-a-website-on-s3_5d4474f9)

---

## Bucket Policies

---

---
