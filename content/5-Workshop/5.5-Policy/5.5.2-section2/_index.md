---
title: "Initialize Elastic Beanstalk"
date: "2025-11-11"
weight: 2
chapter: false
pre: " <b> 5.5.2 </b> "
---

#### Initialize Elastic Beanstalk

We will create the application runtime environment.

1. Access **Elastic Beanstalk** > **Create application**

![EB1](/images/5-Workshop/5.5-Policy/EB1.png)

2. Configure Application:
   - **App Name**: MiniMarket-App
   - **Platform**: Docker (Amazon Linux 2023)
   - **Application code**: Select Sample application (To test infrastructure first)

![EB2](/images/5-Workshop/5.5-Policy/EB2.png)

![EB3](/images/5-Workshop/5.5-Policy/EB3.png)

3. **Network Configuration (Networking)** - Extremely important:
   - **VPC**: Select the VPC you created for MiniMarket
   - **Instance settings**:
     - **Public IP address**: Uncheck
     - **Subnets**: Select 2 Private Subnets
     - **EC2 security groups**: Select sg-web-app

![EB4](/images/5-Workshop/5.5-Policy/EB4.png)

![EB5](/images/5-Workshop/5.5-Policy/EB5.png)

4. **Capacity**:
   - **Environment type**: Select Load balanced

![EB6](/images/5-Workshop/5.5-Policy/EB6.png)

5. **Load balancer network settings**:
   - **Visibility**: Public
   - **Subnets**: Select 2 Public Subnets

![EB7](/images/5-Workshop/5.5-Policy/EB7.png)

6. Click **Create**. The system will take approximately **5-7 minutes** to initialize.
