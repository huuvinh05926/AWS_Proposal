---
title: "Clean up resources"
date: "2025-11-11"
weight: 9
chapter: false
pre: " <b> 5.9. </b> "
---

#### Clean up resources

#### Overview

Congratulations on successfully migrating and deploying the **Human Resources Management (HRM) System** to AWS Cloud infrastructure!

However, our work is not yet complete. The final and most important step to protect your budget is to **Clean up Resources** deployed during the Workshop.

The services we used such as **Amazon RDS for PostgreSQL**, **NAT Gateway**, **Elastic Load Balancer (ELB)**, **AWS ElastiCache (Redis)**, and **EC2 Instances** running the Java Spring Boot application are all charged hourly, whether you use the application or not. If you forget to delete them, the monthly bill can be very high.

We will perform a **Decommissioning (deactivation/removal)** process of the system in the proper sequence to ensure that no resources are left behind causing hidden costs.

#### Content

- [Safe resource deletion procedure](5.9.1-subsection1/)
