---
title: "AWS Account & Services"
date: "2019-05-25"
categories: 
  - "aws"
  - "blog"
  - "js"
  - "music"
tags: 
  - "aws"
  - "aws-cli"
  - "aws-console"
  - "aws-iam"
  - "ecs"
  - "iam-policies"
---

In [my last post](https://blinkhorn.net/blog/aws-certification-why-and-how/), I described why and how I would prepare for my AWS Certified Developer - Associate level exam. I've made it through almost half of that Linux Academy course's material and I'm impressed by how in-depth the instructor goes. I've learned everything from AWS fundamentals to Elastic Container Service (ECS) so far, but as the title to this post suggests, I'm going to recap what I've learned about AWS Account & Services.

* * *

Soundtrack: Patrick [Blinkhorn](https://soundcloud.com/blinkhorn), “Darkness”

<iframe width="100%" height="300" scrolling="no" frameborder="no" allow="autoplay" src="https://w.soundcloud.com/player/?url=https%3A//api.soundcloud.com/tracks/70200877&amp;color=%23ff5500&amp;auto_play=false&amp;hide_related=false&amp;show_comments=true&amp;show_user=true&amp;show_reposts=false&amp;show_teaser=true&amp;visual=true"></iframe>

* * *

When you first create your AWS Account, a "root" user is created, which has full administrative access and rights to every part of your AWS account. However, best practice dictates that you shouldn't use your account's root user for regular AWS admin work; instead, you should create another admin user using IAM (Identity & Access Management -- I'll get to that later in this post) and sign in as that user for regular admin work. It's also a good idea to protect your root user with multi-factor authentication (MFA).

There are three ways to connect to and work with AWS: the AWS Console, AWS CLI, and AWS SDKs. The Linux Academy course focuses on the AWS Console and hasn't elaborated much on AWS SDKs yet. All actions/commands done in the Console and in the CLI are API calls. The CLI also requires API Key configuration.

Earlier I mentioned that you should create an admin using Identity & Access Management (IAM -- often pronounced "I AM") to do your regular admin work. IAM is a core AWS function since we use it to create all the AWS users who will have varying degrees of access to our production account. In addition to creating new users, IAM is used to manage AWS users, groups, and roles and their access to AWS accounts and services. New IAM users have non-explicit deny rules set to them, which means that they have no access to AWS services. In order for the IAM users to have permissions on AWS, they must be granted access through IAM policies. While we can grant permissions to IAM users through IAM policies, best practice is to follow the "principal of least privilege" when administering AWS accounts, users, groups, and roles.

In the above paragraph, I mentioned groups and roles. Groups allow you to assign IAM permission policies to more than one user at a time, which makes administering users' access to AWS resources much easier. Roles are similar to IAM policies, but they are reserved for "entities" such as an AWS resource (e.g. an EC2 instance) or a non-AWS account holder who needs temporary access to an AWS resource.

I've described IAM policies as a means to grant users access to AWS resources. IAM policies are documents that formally state one or more permissions -- they are formatted in JSON. Within the document, an "explicit deny" will always override an "explicit allow," which makes it possible to lock down a user's access by specifying a "deny all" policy. There are pre-built IAM policies such as administrator access which grants full access to AWS resources and read only access, which only allows users to view resources; in addition, you can create policies either from scratch or by using the policy generator. More than one policy may be attached to a user or group at the same time, but they can't be directly attached to AWS resources.

IAM API Keys and IAM Security Token Service (STS) are also notable aspects under the IAM category, but I'll save these for another post. AWS Key Management Service (KMS), Amazon Inspector, and Amazon Cognito are also indirectly related to IAM, but I'll touch on those in a future post as well.
