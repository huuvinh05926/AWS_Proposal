---
title: "Khởi tạo Amazon RDS"
date: "2025-11-11"
weight: 2
chapter: false
pre: " <b> 5.4.2 </b> "
---

#### Khởi tạo Amazon RDS

1. Truy cập **RDS Console** > **Subnet groups** > **Create DB subnet group**

2. Cấu hình Subnet Group:
   - **Name**: db-private-group
   - **Subnets**: Chọn 2 AZ và chọn đúng 2 Private Subnet

![DB1](/images/5-Workshop/5.4-S3-onprem/db1.png)

![DB3](/images/5-Workshop/5.4-S3-onprem/db3.png)

3. Vào **Databases** > **Create database**

![DB4](/images/5-Workshop/5.4-S3-onprem/db4.png)

4. Cấu hình Database:

**Engine options**: Microsoft SQL Server (Express Edition)

![DB5](/images/5-Workshop/5.4-S3-onprem/db5.png)

**Templates**: Free tier

**Settings**: Đặt mật khẩu **Master Password** (ghi nhớ để dùng sau này)

![DB6](/images/5-Workshop/5.4-S3-onprem/db6.png)

**Connectivity**:

- **VPC**: VPC mà bạn đã tạo cho Web
- **Subnet group**: db-private-group
- **Public access**: No
- **VPC security group**: Chọn Security group mà bạn tạo cho database

![DB7](/images/5-Workshop/5.4-S3-onprem/db7.png)

5. Bấm **Create database**
