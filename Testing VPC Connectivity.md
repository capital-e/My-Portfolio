<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Testing VPC Connectivity

**Project Link:** [View Project](http://learn.nextwork.org/projects/aws-networks-connectivity)

**Author:** Jonathan Nutsugah  
**Email:** nutsugahjonathan@gmail.com

---

## Testing VPC Connectivity

![Image](http://learn.nextwork.org/amused_pink_zesty_alpaca/uploads/aws-networks-connectivity_8ee57662)

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

## Connecting to an EC2 Instance

Connectivity means how well devices, systems, or networks can communicate and exchange data with each other. In my case, it refers to how things like EC2 instances, databases, or other services in my VPC are linked and able to interact.

My first connectivity test was whether I could connect to the public server.

![Image](http://learn.nextwork.org/amused_pink_zesty_alpaca/uploads/aws-networks-connectivity_88727bef)

---

## EC2 Instance Connect

I connected to my EC2 instance using EC2 Instance Connect, which is a feature in AWS that lets me securely connect to my EC2 instances using a web-based SSH client right from the AWS Console

My first attempt at getting direct access to my public server resulted in an error because my security group was not configured to allow SSH traffic.

I fixed this error by adding an inbound rule that allows SSH traffic from anywhere.

![Image](http://learn.nextwork.org/amused_pink_zesty_alpaca/uploads/aws-networks-connectivity_1cbb1b88)

---

## Connectivity Between Servers

Ping is a networking utility used to test reachability. I used ping to test the connectivity between my public and private servers.

The ping command I ran was ping 192.168.1.28

The first ping returned nothing. This meant the private server was not reachable.

![Image](http://learn.nextwork.org/amused_pink_zesty_alpaca/uploads/aws-networks-connectivity_defghijk)

---

## Troubleshooting Connectivity

I troubleshooted this by checking the NACLs and security groups to see if any rules were denying my ICMP packets.

![Image](http://learn.nextwork.org/amused_pink_zesty_alpaca/uploads/aws-networks-connectivity_4a9e8014)

---

## Connectivity to the Internet

curl is a command-line tool used to transfer data to or from a server using various protocols like HTTP, HTTPS, FTP, and more. It's commonly used to make API requests, download files, or test server responses.



I used curl to test the connectivity between my public server and the internet.

### Ping vs Curl

Ping and curl are different because ping checks if a server is reachable (network connection), while curl interacts with the server’s applications (like websites or APIs).



---

## Connectivity to the Internet

I ran the curl command curl https://learn.nextwork.org/projects/aws-host-a-website-on-s3, which returned the website.

![Image](http://learn.nextwork.org/amused_pink_zesty_alpaca/uploads/aws-networks-connectivity_8ee57662)

---

---
