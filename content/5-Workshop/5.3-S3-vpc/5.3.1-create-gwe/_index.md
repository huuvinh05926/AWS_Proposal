---
title: "Initialize VPC & Subnets"
date: "2025-11-11"
weight: 1
chapter: false
pre: " <b> 5.3.1 </b> "
---

#### Initialize VPC & Subnets

1. Open the **Amazon VPC console** (Note: Select the appropriate region for your needs, here we use Region **ap-southeast-1**)

2. Choose **Create VPC**

![VPC Tutorial 1](/images/5-Workshop/5.3-S3-vpc/vpc-tutorial-1.png)

3. Configuration:
   - **Name**: MiniMarket-VPC
   - **IPv4 CIDR**: 10.0.0.0/16

![VPC Tutorial 2](/images/5-Workshop/5.3-S3-vpc/vpc-tutorial-2.png)

4. Create **Subnets** (Divide into 2 AZs to ensure High Availability):
   - **Public Subnets (2)**: 10.0.1.0/24 & 10.0.2.0/24 (Used for Load Balancer & NAT)
   - **Private Subnets (2)**: 10.0.3.0/24 & 10.0.4.0/24 (Used for App, DB, Redis)

![VPC Tutorial 3](/images/5-Workshop/5.3-S3-vpc/vpc-tutorial-3.png)

5. Click **Create VPC** and wait for the state to change to **Available** to complete successfully

![VPC Created](/images/5-Workshop/5.3-S3-vpc/vpc-tutorial-4.png)
