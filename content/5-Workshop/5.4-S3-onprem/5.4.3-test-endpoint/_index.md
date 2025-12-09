---
title: "Initialize ElastiCache Redis"
date: "2025-11-11"
weight: 3
chapter: false
pre: " <b> 5.4.3 </b> "
---

#### Initialize ElastiCache Redis

1. Access **ElastiCache** > **Subnet groups** > **Create subnet group**

   - **Name**: redis-private-group
   - **Subnets**: Select 2 Private Subnets

![Elasti1](/images/5-Workshop/5.4-S3-onprem/Elasti1.png)

![Elasti2](/images/5-Workshop/5.4-S3-onprem/Elasti2.png)

2. Go to **Redis OSS caches** > **Create cache**

![Elasti2.9](/images/5-Workshop/5.4-S3-onprem/Elasti2.9.png)

3. In the **Cluster settings** screen:
   - **Engine**: Select Redis OSS
   - **Deployment option**: Select Node-based cluster
   - **Creation method**: Select Cluster cache (Configure and create a new cluster)
   - **Cluster mode**: Select Disabled (Simple mode, 1 Shard)

![Elasti3](/images/5-Workshop/5.4-S3-onprem/Elasti3.png)

4. In the **Location** screen:

   - **Location**: AWS Cloud
   - **Multi-AZ**: Uncheck (Enable)
     - **Note**: Disable this feature to save costs for Lab environment
   - **Auto-failover**: Uncheck (Enable)

5. In the **Cache settings** screen:
   - **Engine version**: Keep default (e.g., 7.1)
   - **Port**: 6379
   - **Node type**: Select t3 line > Select cache.t3.micro
   - **Number of replicas**: Enter 0 (We only need 1 primary node, no backup nodes)

![Elasti4](/images/5-Workshop/5.4-S3-onprem/Elasti4.png)

6. In the **Connectivity** screen:
   - **Network type**: IPv4
   - **Subnet groups**: Select Choose existing subnet group > Select the newly created redis-private-group

![Elasti5](/images/5-Workshop/5.4-S3-onprem/Elasti5.png)

7. In the **Advanced settings** screen (Important):
   - **Encryption at rest**: Enable (Default)
   - **Encryption in transit**: Uncheck (Disable)
     - **Reason**: Disabling transit encryption simplifies connection from .NET code in the internal VPC environment without requiring complex SSL certificate configuration
   - **Selected security groups**: Select Manage > select sg-redis-cache (Uncheck default)

![Elasti6](/images/5-Workshop/5.4-S3-onprem/Elasti6.png)

8. Scroll to the bottom and click **Create**

#### Get Connection Information

1. The initialization process will take approximately **5-10 minutes**

2. When the status changes to **Available** (Green):
   - Click on the Cluster name (webapp or the name you set)
   - In the **Overview** tab, find the **Primary endpoint** section
   - Copy this connection string (Example: webapp.xxxx.cache.amazonaws.com)

![Elasti7](/images/5-Workshop/5.4-S3-onprem/Elasti7.png)

{{% notice tip %}}
This endpoint will be used to configure the `ConnectionStrings__RedisConnection` environment variable for Elastic Beanstalk in the following steps.
{{% /notice %}}
