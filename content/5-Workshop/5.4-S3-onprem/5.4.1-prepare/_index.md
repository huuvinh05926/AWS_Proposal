---
title: "Setup Security Groups"
date: "2025-11-11"
weight: 1
chapter: false
pre: " <b> 5.4.1 </b> "
---

#### Setup Security Groups

1. Access **EC2** > **Security Groups** > **Create security group**

![Security1](/images/5-Workshop/5.4-S3-onprem/security1.png)

![Security2](/images/5-Workshop/5.4-S3-onprem/security2.png)

#### Group 1: Web Server (sg-web-app)

- **Description**: Allow HTTP from the Internet
- **Inbound Rules**:
  - **Type**: HTTP (80) | **Source**: 0.0.0.0/0 (Or only from Load Balancer for stricter security)

![Security3](/images/5-Workshop/5.4-S3-onprem/security3.png)

#### Group 2: Database (sg-db-sql)

- **Description**: Only allow access from Web Server
- **Inbound Rules**:
  - **Type**: MSSQL (1433) | **Source**: Custom > Select sg-web-app ID

![Security4](/images/5-Workshop/5.4-S3-onprem/security4.png)

#### Group 3: Redis Cache (sg-redis-cache)

- **Description**: Only allow access from Web Server
- **Inbound Rules**:
  - **Type**: Custom TCP (6379) | **Source**: Custom > Select sg-web-app ID

![Security5](/images/5-Workshop/5.4-S3-onprem/security5.png)

![add route](/images/5-Workshop/5.4-S3-onprem/add-route.png)

6. Click Save changes
