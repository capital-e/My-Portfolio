<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Create S3 Buckets with Terraform

**Project Link:** [View Project](http://learn.nextwork.org/projects/aws-devops-terraform1)

**Author:** Jonathan Nutsugah  
**Email:** nutsugahjonathan@gmail.com

---

![Image](http://learn.nextwork.org/amused_pink_zesty_alpaca/uploads/aws-devops-terraform1_9i0j1k2l)

---

## Introducing Today's Project!

In this project, I will demonstrate how to use Terraform to automate the creation of cloud resources—in this case, an S3 bucket in AWS. The goal is to learn how Infrastructure as Code works, install and configure Terraform, set up AWS credentials, write a Terraform configuration, and deploy an S3 bucket from my terminal instead of creating it manually. This helps me understand how DevOps teams automate cloud environments to improve efficiency and reduce errors.

### Tools and concepts

In this project, I learned how to use several important cloud and DevOps tools and concepts. I worked with Terraform to define and automate infrastructure using code, and I used AWS S3 as the cloud storage service I deployed through Terraform. I also learned how to install and configure the AWS CLI, generate and use AWS access keys, and authenticate Terraform so it can manage resources in my AWS account. Key concepts included Infrastructure as Code, providers, resource blocks, initialization, planning, and applying configurations. Overall, I learned how automation makes cloud deployments more consistent, repeatable, and efficient.

### Project reflection

It took me about 1 hour to complete this project, including installing the tools, setting up my configuration, fixing credential issues, deploying the S3 bucket, and completing the secret mission.

I chose to do this project today because I wanted hands-on practice with Terraform and AWS, and this walkthrough gave me a clear, structured way to build real cloud infrastructure on my own.

---

## Introducing Terraform

Terraform is a tool that lets me build and manage cloud infrastructure using code instead of clicking through the AWS console. It allows me to describe the resources I want—like servers, networks, and S3 buckets—in simple configuration files, and then Terraform automatically creates or updates those resources for me.

Terraform is one of the most popular tools used for infrastructure as code (IaC), which is the practice of managing and provisioning cloud resources using text-based configuration files instead of doing everything manually in the cloud console. By writing my infrastructure in code, I can version-control it, share it, reuse it, and recreate the same environment consistently whenever I need to. It makes cloud setup more reliable, repeatable, and automated.

main.tf is the primary configuration file in a Terraform project. It’s where I describe the infrastructure I want Terraform to create—in this case, my AWS S3 bucket. Terraform reads this file to understand the desired state of my resources and then uses it to build, update, or manage them.

![Image](http://learn.nextwork.org/amused_pink_zesty_alpaca/uploads/aws-devops-terraform1_9i0j1k2l)

---

## Configuration files

My configuration in Terraform is defined using blocks of code that describe the resources I want to create and the provider I’m using. Each block has a specific purpose—like the provider block that tells Terraform to use AWS, and the resource blocks that define things like my S3 bucket and its settings. Writing the configuration this way lets Terraform understand the desired state of my infrastructure and automatically create or manage the resources to match what I’ve written.

### My main.tf configuration has three blocks

The three blocks in my main.tf file each describes a key part of my Terraform configuration:

provider "aws" – This block tells Terraform that I’m using AWS as my cloud provider and specifies the region where my resources should be created.

resource "aws_s3_bucket" "my_bucket" – This block defines the actual S3 bucket I want Terraform to create. It includes the bucket’s name and serves as the main resource being deployed.

resource "aws_s3_bucket_public_access_block" "my_bucket_public_access_block" – This block configures the public access settings for my S3 bucket. It ensures the bucket is not publicly accessible by blocking public ACLs and policies.

Together, these blocks describe what cloud provider I'm using, what resource I want created, and how that resource should be secured.

![Image](http://learn.nextwork.org/amused_pink_zesty_alpaca/uploads/aws-devops-terraform1_ljvh9876)

---

## Customizing my S3 Bucket

For my project extension, I visited the official Terraform documentation to better understand how Terraform providers and resources are structured, and to confirm that the syntax I used in my main.tf file matches best practices. The documentation shows detailed explanations of each resource type, examples of how to configure them, and descriptions of all available arguments and attributes. It also provides guidance on different features like state management, modules, and variable usage. This helps me understand not just what the code does, but why it works the way it does.

For my customization, I chose to add tags to my S3 bucket. I added a Name tag to label the bucket clearly and an Environment tag set to “Dev” to show that this bucket is for development purposes. These tags help organize and identify resources more easily within AWS.

![Image](http://learn.nextwork.org/amused_pink_zesty_alpaca/uploads/aws-devops-terraform1_ffe757cd3)

---

## Terraform commands

terraform init sets up my Terraform project so I can start working with it. It downloads the necessary provider plugins—in this case, the AWS provider—and prepares the backend and any modules the project might use. Basically, it gets my working directory ready so Terraform can read my configuration and know how to communicate with AWS.

terraform plan creates a preview of the changes Terraform will make to my AWS environment based on the configuration in my files. It shows which resources will be created, updated, or destroyed before anything is actually applied. This gives me a chance to review the planned actions and confirm that everything looks correct before making real changes in my AWS account.

![Image](http://learn.nextwork.org/amused_pink_zesty_alpaca/uploads/aws-devops-terraform1_3g4h5i6j)

---

## AWS CLI and Access Keys

This error means Terraform doesn't have the necessary credentials to access your AWS account. We need to configure AWS credentials for Terraform to use, so that it can create AWS resources on our behalf.

The AWS CLI is a command-line tool that lets me interact with AWS services directly from my terminal instead of using the AWS Management Console. It allows me to run commands to configure settings, create resources, and manage my AWS environment programmatically. In this project, I’m using the AWS CLI so Terraform can authenticate and communicate with my AWS account using the access keys I configure.

I set up access keys so that my local machine—and specifically Terraform—can authenticate with my AWS account. Since the AWS CLI and Terraform can’t use the login from the web console, they need a programmatic way to verify my identity. The access key and secret access key act like a secure username and password for command-line access, allowing Terraform to create and manage resources in my AWS account on my behalf.

![Image](http://learn.nextwork.org/amused_pink_zesty_alpaca/uploads/aws-devops-terraform1_7j8k9l0m)

---

## Lanching the S3 Bucket

terraform apply takes the changes shown in the plan and actually executes them in my AWS account. It creates, updates, or deletes resources so that my real AWS environment matches the configuration I wrote in my Terraform files. In this project, running terraform apply triggers the creation of my S3 bucket and its public access settings.

The Terraform commands follow a logical order that reflects how infrastructure is prepared, reviewed, and deployed:

terraform init is always run first. It prepares the working directory by downloading providers and setting up everything Terraform needs to work with my configuration.

terraform plan comes next. It analyzes my configuration and compares it to the current state of my AWS environment, then shows me exactly what changes Terraform intends to make. This lets me review and confirm that everything looks correct.

terraform apply is the final step. It takes the plan and carries out those actions, creating or updating the resources in AWS so my environment matches my configuration.

Together, these commands ensure that my infrastructure is properly set up, validated, and safely executed.

![Image](http://learn.nextwork.org/amused_pink_zesty_alpaca/uploads/aws-devops-terraform1_1q2w3e4r)

---

## Uploading an S3 Object

I added a new resource block so Terraform could manage more than just the S3 bucket itself. By creating an additional block—for example, an aws_s3_object resource—I can instruct Terraform to upload a specific file into my bucket automatically. This demonstrates how Terraform can control both the infrastructure and the objects inside it, keeping everything managed consistently through code.

We need to run terraform apply again because I changed my Terraform configuration by adding a new resource. Whenever the configuration is updated, Terraform needs to re-evaluate the desired state and then apply those changes to the actual AWS environment. Running terraform apply ensures that the new resource—like the S3 object I added—is created and synced with what I defined in my code.

I validated my object upload by going to the S3 console in the AWS Management Console, opening the bucket that Terraform created, and confirming that the file I specified in my configuration appeared inside the bucket. I then selected the file, downloaded it, and opened it on my computer to make sure it matched the original file I uploaded. This confirmed that Terraform successfully uploaded the object to my S3 bucket.

![Image](http://learn.nextwork.org/amused_pink_zesty_alpaca/uploads/aws-devops-terraform1_9o0p1a2s)

---

---
