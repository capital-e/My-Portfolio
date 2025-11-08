<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Cloud Security with AWS IAM

**Project Link:** [View Project](http://learn.nextwork.org/projects/aws-security-iam)

**Author:** Jonathan Nutsugah  
**Email:** nutsugahjonathan@gmail.com

---

![Image](http://learn.nextwork.org/amused_pink_zesty_alpaca/uploads/aws-security-iam_1c864649)

---

## Introducing Today's Project!

Today, we’re here to learn how to create and manage EC2 instances, set up IAM policies, create IAM users and groups, and customize our AWS account with an alias—all from scratch.

### Tools and concepts

In this project, I learned how to launch and manage EC2 instances, create and apply IAM policies, set up IAM users and groups, use account aliases for easier login, and control user access through permissions.

### Project reflection

1 hour 30 minutes.

---

## Tags

Tags are key-value pairs that help you organize and manage AWS resources. They’re useful for tracking costs, identifying resources by purpose, owner, or environment, and simplifying resource management across large projects.

I assigned the following tags to my two EC2 instances:

First EC2 instance: Key = Env, Value = production

Second EC2 instance: Key = Env, Value = development

![Image](http://learn.nextwork.org/amused_pink_zesty_alpaca/uploads/aws-security-iam_2e0e5a5d)

---

## IAM Policies

 IAM Policies define permissions for AWS users, groups, or roles. They control what actions can be performed on which resources, helping enforce security and access control within an AWS environment.

### The policy I set up

For this project, I’ve set up a policy using JSON.

This policy allows some actions (like starting, stopping, and describing EC2 instances) for instances tagged with "Env = development" while denying the ability to create or delete tags for all instances.

### When creating a JSON policy, you have to define its Effect, Action and Resource.

In a JSON IAM policy:
Effect specifies whether the policy allows or denies the action.
Action defines what AWS service operations are allowed or denied
Resource specifies the ARN of the AWS resource the action applies to.

---

## My JSON Policy

![Image](http://learn.nextwork.org/amused_pink_zesty_alpaca/uploads/aws-security-iam_1c864649)

---

## Account Alias

An Account Alias is a custom name that replaces the default AWS account ID in the login URL, making it easier for users to remember and access the AWS Management Console.

Creating an account alias took me a minute. Now, my new AWS console sign-in URL is https://sacnet-jon.signin.aws.amazon.com/console

![Image](http://learn.nextwork.org/amused_pink_zesty_alpaca/uploads/aws-security-iam_0eb4439b)

---

## IAM Users and User Groups

### Users

IAM users are individual identities created within AWS to represent a person or application. Each user has unique credentials and can be assigned specific permissions to access AWS resources securely.

### User Groups

IAM user groups are collections of IAM users that share the same permissions. By assigning policies to a group, you can manage permissions for multiple users at once, making access control simpler and more efficient.

Attaching a policy to a user group grants all users in that group the permissions defined in the policy. This ensures consistent access control and makes it easier to manage permissions for multiple users at once.

---

## Logging in as an IAM User

The two ways to share a new user's sign-in details are:

Email – Send the login credentials directly to the user’s email from the AWS Console setup screen.

Download .csv – Download the user's credentials as a CSV file and share it securely.

I observed that the new IAM user's AWS dashboard had limited access—only the services and actions allowed by the attached IAM policy were visible. This confirmed that the user's permissions were correctly restricted to their role.

![Image](http://learn.nextwork.org/amused_pink_zesty_alpaca/uploads/aws-security-iam_6f2ab446)

---

## Testing IAM Policies

I tested my JSON IAM policy by attempting to stop both EC2 instances. The action was successful on the development instance but denied on the production instance, confirming that the policy correctly limited access as intended.

### Stopping the production instance

When I tried to stop the production instance using the new IAM user, access was denied. This happened because the IAM policy only allowed actions on the development instance, not the production one.

![Image](http://learn.nextwork.org/amused_pink_zesty_alpaca/uploads/aws-security-iam_0e7a9d6a)

---

## Testing IAM Policies

### Stopping the development instance

When I tried to stop the development instance, the action was successful. This confirmed that the IAM policy correctly granted the necessary permissions for that instance.

![Image](http://learn.nextwork.org/amused_pink_zesty_alpaca/uploads/aws-security-iam_1811801c)

---

## The IAM Policy Simulator

### How I used the simulator

---

---
