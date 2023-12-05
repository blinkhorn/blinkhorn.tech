---
title: "AWS IAM API Keys & STS"
date: "2019-05-26"
categories: 
  - "aws"
  - "music"
tags: 
  - "aws"
  - "aws-cli"
  - "iam"
  - "iam-api-keys"
  - "security-token-service"
  - "sts"
---

I gave an overview of IAM (Identity & Access Management) in [my last post](https://blinkhorn.tech/blog/aws-account-services/), but I left two concepts out: IAM API Keys and STS (Security Token Service). This brief post will be devoted to IAM API Keys and STS.

* * *

Soundtrack: Blinkhorn - "Music for Rainy Days"

<iframe style="border: 0; width: 400px; height: 274px;" src="https://bandcamp.com/EmbeddedPlayer/album=2533730195/size=large/bgcol=ffffff/linkcol=0687f5/artwork=small/transparent=true/" seamless><a href="https://blinkhorn.bandcamp.com/album/music-for-rainy-days">Music for Rainy Days by Blinkhorn</a></iframe>

* * * 

IAM API Keys, also known as IAM API Access Keys, are required when making programmatic calls from the AWS CLI, Tools for Windows PowerShell, AWS SDKs, or when you're making direct HTTP calls using the APIs for individual AWS services. For example, API Keys could be used by a developer when working on an on-site network for AWS CLI access. It is important to note that IAM API Keys are only available when a new user is created or when you reissue a new set of keys. AWS will not reissue the same set of IAM API Keys, and in order for the keys to work, they must be associated with a user. If you need new API Keys, you must deactivate your current set before you generate a new one. Finally, you can, but never should create or store API Keys on an EC2 instance, as that poses a security vulnerability.

The IAM Security Token Service, or STS, lets you create temporary security credentials that allow trusted users access to your AWS resources. STS credentials can be active for a few minutes to several hours, and once they expire, your AWS resources will no longer be available via the STS credentials. Credentials are returned with the following three components when requested through an STS API call: a security token, an access key ID, and a secret access key. STS is typically used with roles for AWS resources, roles for cross-account access, or identity federation (either enterprise identity federation or web identity federation).
