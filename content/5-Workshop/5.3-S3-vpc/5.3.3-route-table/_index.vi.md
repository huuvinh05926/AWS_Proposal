---
title: "Cấu hình Route Table"
date: "2025-11-11"
weight: 3
chapter: false
pre: " <b> 5.3.3 </b> "
---

#### Tạo Route Table

1. Ấn vào phần **Route tables** trong VPC dashboard

![RT1](/images/5-Workshop/5.3-S3-vpc/RT1.png)

2. Tạo 2 Route Table, **Public** với **Private**

![RT2](/images/5-Workshop/5.3-S3-vpc/RT2.png)

![RT3](/images/5-Workshop/5.3-S3-vpc/RT3.png)

#### Public Route Table:

1. Đối với **Public Route Table**, trong phần **Routes** ấn vào **Edit routes**

2. Trỏ **0.0.0.0/0** về **Internet Gateway**

![RT4](/images/5-Workshop/5.3-S3-vpc/RT4.png)

![RT5](/images/5-Workshop/5.3-S3-vpc/RT5.png)

3. Và trong phần **Subnet associations**, gán cho cả hai **Public Subnets**

![RT6](/images/5-Workshop/5.3-S3-vpc/RT6.png)

![RT7](/images/5-Workshop/5.3-S3-vpc/RT7.png)

#### Private Route Table:

1. Đối với **Private Route Table**, chúng ta sẽ trỏ **0.0.0.0/0** về **NAT Gateway**

![RT8](/images/5-Workshop/5.3-S3-vpc/RT8.png)

2. Và trong phần **Subnet associations**, gán cho cả hai **Private Subnets**

![RT9](/images/5-Workshop/5.3-S3-vpc/RT9.png)

{{% notice tip %}}
Việc tách biệt Route Table đảm bảo rằng các Database trong Private Subnet không bao giờ bị lộ trực tiếp ra Internet.
{{% /notice %}}
