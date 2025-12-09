---
title: "Create Build Project"
date: "2025-11-11"
weight: 1
chapter: false
pre: " <b> 5.6.1 </b> "
---

#### Create Build Project

1. Access **CodeBuild** > **Create project**

![cicd1](/images/5-Workshop/5.6-Cleanup/cicd1.png)

2. **Project name**: MiniMarket-Build

![cicd2](/images/5-Workshop/5.6-Cleanup/cicd2.png)

3. **Source**: Select **GitHub** (Connect to the repository containing the code)

![cicd3](/images/5-Workshop/5.6-Cleanup/cicd3.png)

4. **Environment**:
   - **Environment image**: Managed Image
   - **Operating system**: Amazon Linux
   - **Runtime**: Standard
   - **Image**: 5.0
   - **Service role**: New service role

![cicd4](/images/5-Workshop/5.6-Cleanup/cicd4.png)

![cicd5](/images/5-Workshop/5.6-Cleanup/cicd5.png)

5. **Privileged**: Enable (Required to run Docker build commands)

![cicd6](/images/5-Workshop/5.6-Cleanup/cicd6.png)

6. **Buildspec**: Use a buildspec file

![cicd7](/images/5-Workshop/5.6-Cleanup/cicd7.png)

7. Click **Create build project**

{{% notice tip %}}
After creation, go to the **IAM Role** of the newly created CodeBuild and grant additional **AmazonEC2ContainerRegistryPowerUser** permission so it can push images to ECR.
{{% /notice %}}
