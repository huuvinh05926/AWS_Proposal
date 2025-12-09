---
title: "Setup CodePipeline"
date: "2025-11-11"
weight: 2
chapter: false
pre: " <b> 5.6.2 </b> "
---

#### Setup CodePipeline

1. Access **CodePipeline** > **Create pipeline**

![pipeline1](/images/5-Workshop/5.6-Cleanup/pipeline1.png)

2. **Category**: Select **Build custom pipeline**

![pipeline2](/images/5-Workshop/5.6-Cleanup/pipeline2.png)

3. **Settings**: Select **New service role**

![pipeline3](/images/5-Workshop/5.6-Cleanup/pipeline3.png)

4. **Source Stage**: Select **GitHub (via GitHub App)** > **Connect to GitHub** > Select the repository and branch you want to deploy to the cloud

![pipeline4](/images/5-Workshop/5.6-Cleanup/pipeline4.png)

5. **Build Stage**: Select **AWS CodeBuild** > Select the **MiniMarket-Build** project you just created

![pipeline5](/images/5-Workshop/5.6-Cleanup/pipeline5.png)

6. **Test Stage**: Click **Skip test stage**

7. **Deploy Stage**:
   - **Provider**: AWS Elastic Beanstalk
   - **Application name**: MiniMarket-App
   - **Environment name**: Select the running environment

![pipeline6](/images/5-Workshop/5.6-Cleanup/pipeline6.png)

8. Click **Create pipeline**

{{% notice warning %}}
If the Deploy step fails with a Permission error, go to the **IAM Role** of CodePipeline and grant **AdministratorAccess-AWSElasticBeanstalk** permission
{{% /notice %}}
