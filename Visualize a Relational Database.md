<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Visualize a Relational Database

**Project Link:** [View Project](http://learn.nextwork.org/projects/aws-databases-rds)

**Author:** Jonathan Nutsugah  
**Email:** nutsugahjonathan@gmail.com

---

## Visualise a Relational Database

![Image](http://learn.nextwork.org/amused_pink_zesty_alpaca/uploads/aws-databases-rds_1fddb0b5)

---

## Introducing Today's Project!

### What is Amazon RDS?

Amazon RDS is a cloud service that makes it easy to set up, operate, and scale a relational database. It’s useful because it handles backups, updates, and maintenance, so I can focus on using the database, not managing it.

### How I used Amazon RDS in this project

I used Amazon RDS to create a MySQL database, set it up with tables and data, and connected it securely to QuickSight to visualize that data with charts.

### One thing I didn't expect in this project was...

I didn’t expect how many security steps were needed—like setting up multiple security groups and making the RDS instance private—to connect everything safely.

### This project took me...

This project took me a few hours, mostly spent setting up the database, configuring security, and troubleshooting the connections between RDS and QuickSight.

---

## In the first part of my project...

### Creating a Relational Database

I used the Easy Create option in AWS RDS. I picked the MySQL database engine, entered a name and username, kept the default settings, and clicked "Create database." AWS handled the rest.

![Image](http://learn.nextwork.org/amused_pink_zesty_alpaca/uploads/aws-databases-rds_43343546)

---

## Understanding Relational Databases

A relational database is a type of database that stores data in tables with rows and columns. Each table holds related data, and the tables can be linked by shared values, like IDs. This structure makes it easy to organize, search, and connect data.

### MySQL vs SQL

SQL is the language used to manage and query databases.
MySQL is a relational database system that uses SQL.

So:
SQL = the language (Structured Query Language)
MySQL = the software that runs a database and understands SQL


---

## Populating my RDS instance

I made the RDS instance public so my local computer, which is outside the AWS network, can connect to it using MySQL Workbench.

I updated the security group to allow traffic from my local IP address. Without this, AWS would block the connection for security reasons.

![Image](http://learn.nextwork.org/amused_pink_zesty_alpaca/uploads/aws-databases-rds_91b9fd1g)

---

## Using MySQL Workbench

![Image](http://learn.nextwork.org/amused_pink_zesty_alpaca/uploads/aws-databases-rds_1fddb0b5)

I wrote and ran SQL INSERT statements in MySQL Workbench to add data into my tables.

---

## Connecting QuickSight and RDS

I added QuickSight’s IP range to my RDS security group to allow access. Then in QuickSight, I chose RDS as a data source, entered the database info, and connected it successfully.

The risk is that my RDS instance is publicly accessible, which means anyone on the internet could try to connect. This makes it vulnerable to hacking, unauthorized access, and data breaches.

### A better strategy

This new security group is for QuickSight. It controls and secures how QuickSight connects to my RDS instance within the VPC.

I created a new IAM policy called QuickSightAllowVPC, then went back to the QuickSight VPC connection and added the new security group. After that, the connection worked!

---

## Now to secure my RDS instance

 I created a new security group called RDS_SecGp in the default VPC, then added an inbound rule to allow MySQL traffic from the QuickSight security group. This lets QuickSight access RDS securely without making it public.

I created a new security group for RDS, added an inbound MySQL rule allowing access from the QuickSight security group, and then attached this new group to my RDS instance by modifying its settings.

![Image](http://learn.nextwork.org/amused_pink_zesty_alpaca/uploads/aws-databases-rds_1709b26b)

---

## Adding RDS as a data source for QuickSight

![Image](http://learn.nextwork.org/amused_pink_zesty_alpaca/uploads/aws-databases-rds_1709b29b)

Now my data source connects securely through a private VPC using security groups, not the public internet. It’s safer and only accessible to approved AWS services like QuickSight.

![Image](http://learn.nextwork.org/amused_pink_zesty_alpaca/uploads/aws-databases-rds_1709b30b)

---

---
