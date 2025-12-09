---
title: "Clean up resources"
date: "2025-11-11"
weight: 1
chapter: false
pre: " <b> 5.9.1 </b> "
---

#### Clean up resources

To avoid unexpected costs after completing the Workshop, delete resources in the following order:

**1. NAT Gateway**: **Delete NAT Gateway** > Wait for **Deleted** > **Release Elastic IP** (Most important as this costs the most)

![DEL1](/images/5-Workshop/5.9-Section9/DEL1.png)

![DEL2](/images/5-Workshop/5.9-Section9/DEL2.png)

**2. Elastic Beanstalk**: **Terminate Environment**

![DEL3](/images/5-Workshop/5.9-Section9/DEL3.png)

**3. ElastiCache**: **Delete Redis Cluster** (Uncheck Create Backup)

![DEL4](/images/5-Workshop/5.9-Section9/DEL4.png)

**4. RDS**: **Stop** (or **Delete** if no longer needed - remember to uncheck Final Snapshot).

![DEL5](/images/5-Workshop/5.9-Section9/DEL5.png)

**5. WAF**: **Manage resources** > **Disassociate** > **Delete protection pack (web ACL)**

![DEL7](/images/5-Workshop/5.9-Section9/DEL7.png)

![DEL6](/images/5-Workshop/5.9-Section9/DEL6.png)

**6. S3**: **Empty** and **Delete Bucket** (Can keep if still in use as the cost is not too high)

**7. CloudFront**: **Disable** and **Delete**
