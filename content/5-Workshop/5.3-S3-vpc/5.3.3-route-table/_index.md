---
title: "Configure Route Table"
date: "2025-11-11"
weight: 3
chapter: false
pre: " <b> 5.3.3 </b> "
---

#### Create Route Table

1. Click on **Route tables** in the VPC dashboard

![RT1](/images/5-Workshop/5.3-S3-vpc/RT1.png)

2. Create 2 Route Tables, **Public** and **Private**

![RT2](/images/5-Workshop/5.3-S3-vpc/RT2.png)

![RT3](/images/5-Workshop/5.3-S3-vpc/RT3.png)

#### Public Route Table:

1. For the **Public Route Table**, in the **Routes** section, click on **Edit routes**

2. Point **0.0.0.0/0** to the **Internet Gateway**

![RT4](/images/5-Workshop/5.3-S3-vpc/RT4.png)

![RT5](/images/5-Workshop/5.3-S3-vpc/RT5.png)

3. In the **Subnet associations** section, assign both **Public Subnets**

![RT6](/images/5-Workshop/5.3-S3-vpc/RT6.png)

![RT7](/images/5-Workshop/5.3-S3-vpc/RT7.png)

#### Private Route Table:

1. For the **Private Route Table**, we will point **0.0.0.0/0** to the **NAT Gateway**

![RT8](/images/5-Workshop/5.3-S3-vpc/RT8.png)

2. In the **Subnet associations** section, assign both **Private Subnets**

![RT9](/images/5-Workshop/5.3-S3-vpc/RT9.png)

{{% notice tip %}}
Separating Route Tables ensures that Databases in the Private Subnet are never directly exposed to the Internet.
{{% /notice %}}
