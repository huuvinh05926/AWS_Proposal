---
title: "Initialize Amazon RDS"
date: "2025-11-11"
weight: 2
chapter: false
pre: " <b> 5.4.2 </b> "
---

#### Initialize Amazon RDS

1. Access **RDS Console** > **Subnet groups** > **Create DB subnet group**

2. Configure Subnet Group:
   - **Name**: db-private-group
   - **Subnets**: Select 2 AZs and choose the correct 2 Private Subnets

![DB1](/images/5-Workshop/5.4-S3-onprem/db1.png)

![DB3](/images/5-Workshop/5.4-S3-onprem/db3.png)

3. Go to **Databases** > **Create database**

![DB4](/images/5-Workshop/5.4-S3-onprem/db4.png)

4. Configure Database:

**Engine options**: Microsoft SQL Server (Express Edition)

![DB5](/images/5-Workshop/5.4-S3-onprem/db5.png)

**Templates**: Free tier

**Settings**: Set **Master Password** (remember it for later use)

![DB6](/images/5-Workshop/5.4-S3-onprem/db6.png)

**Connectivity**:

- **VPC**: The VPC you created for Web
- **Subnet group**: db-private-group
- **Public access**: No
- **VPC security group**: Select the Security group you created for the database

![DB7](/images/5-Workshop/5.4-S3-onprem/db7.png)

5. Click **Create database**
