---
title: "Cấu hình Biến môi trường"
date: "2025-11-11"
weight: 3
chapter: false
pre: " <b> 5.5.3 </b> "
---

#### Cấu hình Biến môi trường

Để ứng dụng kết nối được với Database và Redis, chúng ta không hardcode trong code mà dùng **Biến môi trường**.

1. Vào **Beanstalk Environment** > **Configuration** > **Updates, monitoring, and logging** > **Edit**

2. Kéo xuống mục **Environment properties**

3. Thêm các biến sau:

**Biến 1:**

- **Name**: `ConnectionStrings__DefaultConnection`
- **Value**: `Server=sql-shop-db….rds.amazonaws.com;Database=MiniMarketDB;User Id=admin;Password=PASSWORD BẠN ĐẶT;TrustServerCertificate=True;`

**Biến 2:**

- **Name**: `ConnectionStrings__RedisConnection`
- **Value**: `webapp.redis.cache…:6379`

**Biến 3:**

- **Name**: `VnPay__IPNUrl`
- **Value**: `https://[cloudfrontdomain].cloudfront.net/Payment/VnPayIPN`

**Biến 4:**

- **Name**: `VnPay__ReturnUrl`
- **Value**: `https://[cloudfrontdomain].cloudfront.net/Payment/VnPayReturn`

![config1](/images/5-Workshop/5.5-Policy/config1.png)

4. Bấm **Apply**. Server sẽ khởi động lại để nhận cấu hình mới.
