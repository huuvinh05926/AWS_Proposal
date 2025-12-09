---
title: "Configure Environment Variables"
date: "2025-11-11"
weight: 3
chapter: false
pre: " <b> 5.5.3 </b> "
---

#### Configure Environment Variables

To enable the application to connect to the Database and Redis, we don't hardcode in the code but use **Environment Variables**.

1. Go to **Beanstalk Environment** > **Configuration** > **Updates, monitoring, and logging** > **Edit**

2. Scroll down to the **Environment properties** section

3. Add the following variables:

**Variable 1:**

- **Name**: `ConnectionStrings__DefaultConnection`
- **Value**: `Server=sql-shop-db….rds.amazonaws.com;Database=MiniMarketDB;User Id=admin;Password=YOUR PASSWORD;TrustServerCertificate=True;`

**Variable 2:**

- **Name**: `ConnectionStrings__RedisConnection`
- **Value**: `webapp.redis.cache…:6379`

**Variable 3:**

- **Name**: `VnPay__IPNUrl`
- **Value**: `https://[cloudfrontdomain].cloudfront.net/Payment/VnPayIPN`

**Variable 4:**

- **Name**: `VnPay__ReturnUrl`
- **Value**: `https://[cloudfrontdomain].cloudfront.net/Payment/VnPayReturn`

![config1](/images/5-Workshop/5.5-Policy/config1.png)

4. Click **Apply**. The server will restart to receive the new configuration.
