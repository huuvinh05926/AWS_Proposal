---
title: "Prerequisites"
date: "2025-11-11"
weight: 2
chapter: false
pre: " <b> 5.2. </b> "
---

#### IAM Permissions

Attach the AdministratorAccess IAM permission policy to your AWS account for easier workflow.

**Note:** Using Administrator permissions is only recommended for Workshop environments to ensure the deployment process is not interrupted. In actual Production environments, the Least Privilege principle must be followed for each service.

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": "*",
      "Resource": "*"
    }
  ]
}
```

#### Source Code

GitHub repository containing valid .NET Core code and Dockerfile.

![Source Code](/images/5-Workshop/5.2-Prerequisite/source-code.png)
