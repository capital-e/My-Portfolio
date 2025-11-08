<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Launching VPC Resources

**Project Link:** [View Project](http://learn.nextwork.org/projects/aws-networks-ec2)

**Author:** Jonathan Nutsugah  
**Email:** nutsugahjonathan@gmail.com

---

## Launching VPC Resources

![Image](http://learn.nextwork.org/amused_pink_zesty_alpaca/uploads/aws-networks-ec2_8ee57662)

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

## Setting Up Direct VM Access

Directly accessing a virtual machine means logging into and managing the operating system or software of the machine as if you were using it in front of you, but over the internet

### SSH is a key method for directly accessing a VM

SSH stands for Secure Shell. It’s a network protocol used to securely connect to remote computers, typically for managing servers. It encrypts data to protect login credentials and communications from being intercepted.









### To enable direct access, I set up key pairs

A key pair in AWS is a set of two cryptographic keys—a public key and a private key—used for securely connecting to EC2 instances. The public key is stored on the instance, and you use the private key (usually in a .pem file) to authenticate via SSH.

A private key's file format means the file type it is stored in. My private key's file format was .pem

---

## Launching a public server

I had to change my EC2 instance's networking settings by clicking on edit and changing the VPC settings and security group settings.

![Image](http://learn.nextwork.org/amused_pink_zesty_alpaca/uploads/aws-networks-ec2_88727bef)

---

## Launching a private server

My private server has its own dedicated security group because I need to limit access to this server. The other security group will be configured to allow more access.

My private server's security group's source is the public security group. which means instances within the public security group can communicate with instances within the private security group.

![Image](http://learn.nextwork.org/amused_pink_zesty_alpaca/uploads/aws-networks-ec2_4a9e8014)

---

## Speeding up VPC creation

I used an alternative way to set up an Amazon VPC! This time, I chose to use the ’VPC and more‘ feature, which allows me to deploy subnets and more.

A VPC resource map is a visual diagram that shows the components and layout of your Amazon VPC.



My new VPC has a CIDR block of 10.0.0.0/16. It is possible for my new VPC to have the same IPv4 CIDR block as my existing VPC because VPCs in AWS are logically isolated.

![Image](http://learn.nextwork.org/amused_pink_zesty_alpaca/uploads/aws-networks-ec2_1cbb1b88)

---

## Speeding up VPC creation

### Tips for using the VPC resource map

When determining the number of public subnets in my VPC, I only had two options: 0 and 2. This was because of best practices for redundancy and availability.

The setup page also offered to create NAT gateways, which are AWS services that allow instances in a private subnet of my VPC to access the internet (for things like software updates) without exposing them to incoming traffic from the internet.

![Image](http://learn.nextwork.org/amused_pink_zesty_alpaca/uploads/aws-networks-ec2_8ee57662)

---

---
