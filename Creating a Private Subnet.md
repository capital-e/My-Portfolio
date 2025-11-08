<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Creating a Private Subnet

**Project Link:** [View Project](http://learn.nextwork.org/projects/aws-networks-private)

**Author:** Jonathan Nutsugah  
**Email:** nutsugahjonathan@gmail.com

---

## Creating a Private Subnet

![Image](http://learn.nextwork.org/amused_pink_zesty_alpaca/uploads/aws-networks-private_afe1fdbd)

---

## Introducing Today's Project!

### What is Amazon VPC?

Amazon VPC (Virtual Private Cloud) lets you create a secure, isolated network in AWS where you control IP ranges, subnets, and traffic. It's useful for customizing network setup, enhancing security, and supporting hybrid cloud deployments.










### How I used Amazon VPC in this project

Through the management console, I used it to virtually isolate a space to keep my resources away from external access.

### One thing I didn't expect in this project was...

How easy it is to navigate AWS.

### This project took me...

40 minutes.

---

## Private vs Public Subnets

The difference between public and private subnets is that public subnets have access to the internet through an internet gateway, while private subnets do not have direct internet access and are typically used for internal resources like databases.

Having private subnets is useful because they enhance security by isolating sensitive resources (like databases or internal services) from direct internet access, reducing the risk of external attacks.










My private and public subnets cannot have the same range of IP addresses.

![Image](http://learn.nextwork.org/amused_pink_zesty_alpaca/uploads/aws-networks-private_afe1fdbd)

---

## A dedicated route table

By default, my private subnet is associated with the local target route.

I had to set up a new route table because the other route table will direct traffic to the internet, and we do not want that.

My private subnet's dedicated route table has only one inbound and one outbound rule, which allows traffic to flow only within the local network.

![Image](http://learn.nextwork.org/amused_pink_zesty_alpaca/uploads/aws-networks-private_b4b904b5)

---

## A new network ACL

By default, my private subnet is associated with the default NACL created for the VPC.

I set up a dedicated network ACL for my private subnet because I want to deny all traffic for now until I am sure which traffic to allow.

My new network ACL has two simple rules - Deny all traffic, both inbound and outbound.

![Image](http://learn.nextwork.org/amused_pink_zesty_alpaca/uploads/aws-networks-private_1ed2cb07)

---

---
