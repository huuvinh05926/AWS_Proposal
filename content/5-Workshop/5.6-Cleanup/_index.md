---
title: "Automate CI/CD"
date: "2025-11-11"
weight: 6
chapter: false
pre: " <b> 5.6. </b> "
---

#### Overview

In a Cloud Native environment, manual deployment is risky and time-consuming. This module will guide you through building a fully automated **CI/CD (Continuous Integration / Continuous Deployment)** workflow.

**The workflow operates as follows:**

1. **Source**: Developer pushes code to GitHub
2. **Build**: AWS CodePipeline detects changes and triggers AWS CodeBuild. CodeBuild packages the Docker Image and pushes it to the Amazon ECR repository
3. **Deploy**: Pipeline automatically instructs Elastic Beanstalk to update to the latest version from ECR without causing service interruption

![CI/CD Pipeline](/images/5-Workshop/5.6-Cleanup/cicd-pipeline.png)

#### Content

- [Create Build Project with AWS CodeBuild](5.6.1-section1/)
- [Setup AWS CodePipeline](5.6.2-section2/)

#### clean up

1. Navigate to Hosted Zones on the left side of Route 53 console. Click the name of _s3.us-east-1.amazonaws.com_ zone. Click Delete and confirm deletion by typing delete.

![hosted zone](/images/5-Workshop/5.6-Cleanup/delete-zone.png)

2. Disassociate the Route 53 Resolver Rule - myS3Rule from "VPC Onprem" and Delete it.

![hosted zone](/images/5-Workshop/5.6-Cleanup/vpc.png)

4. Open the CloudFormation console and delete the two CloudFormation Stacks that you created for this lab:

- PLOnpremSetup
- PLCloudSetup

![delete stack](/images/5-Workshop/5.6-Cleanup/delete-stack.png)

5. Delete S3 buckets

- Open S3 console
- Choose the bucket we created for the lab, click and confirm empty. Click delete and confirm delete.

![delete s3](/images/5-Workshop/5.6-Cleanup/delete-s3.png)
