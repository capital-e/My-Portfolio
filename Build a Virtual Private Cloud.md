<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Build a Virtual Private Cloud

**Project Link:** [View Project](http://learn.nextwork.org/projects/aws-networks-vpc)

**Author:** Jonathan Nutsugah  
**Email:** nutsugahjonathan@gmail.com

---

## Build a Virtual Private Cloud (VPC)

![Image](http://learn.nextwork.org/amused_pink_zesty_alpaca/uploads/aws-networks-vpc_2facf927)

---

## Introducing Today's Project!

### What is Amazon VPC?

Amazon VPC is a service used to create and manage isolated cloud resources. It is useful because we want to be able to keep our resources in one place where we can easily find and manage them away from external access.

### How I used Amazon VPC in this project

I accessed it through the management console and used it to build an internal network for my resources.

### One thing I didn't expect in this project was...

How easy it is to navigate the UI.

### This project took me...

Barely 10 minutes.

---

## Virtual Private Clouds (VPCs)

VPCs are isolated environments in which users can keep resources away from the public. They are like internal networks.

There was already a default VPC in my account ever since my AWS account was created. This is because AWS wants it to be faster and easier to deploy resources, especially for beginners.

To set up my VPC, I had to define an IPv4 CIDR block, which is a range of IPv4 addresses available to be assigned to any resource deployed in the VPC. This is done to enable resources to communicate with each other.

![Image](http://learn.nextwork.org/amused_pink_zesty_alpaca/uploads/aws-networks-vpc_2facf927)

---

## Subnets

Subnets are smaller networks within the VPC. There are already subnets existing in my account, one for every availability zone.

Once I created my subnet, I enabled auto-assign public IPv4 addresses. This setting makes sure addresses are automatically assigned to resources deployed in the subnet so that we don't have to configure them separately for each deployed resource.

The difference between public and private subnets is their ability to communicate with the Internet. For a subnet to be considered public, it has to be provided with an internet gateway.

![Image](http://learn.nextwork.org/amused_pink_zesty_alpaca/uploads/aws-networks-vpc_157c4219)

---

## Internet gateways

Internet gateways are the bridge between the isolated resources in the VPC and the public internet.

Attaching an internet gateway to a VPC means resources can now communicate with the internet. If I missed this step, there will be no internet connectivity.

![Image](http://learn.nextwork.org/amused_pink_zesty_alpaca/uploads/aws-networks-vpc_4ae90410)

---

## Using the AWS CLI

---

---
