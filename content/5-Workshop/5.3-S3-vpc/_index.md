---
title: "Network Infrastructure Setup"
date: "2025-11-11"
weight: 3
chapter: false
pre: " <b> 5.3. </b> "
---

#### 💡 Overview

In this initial phase, we will build a solid and secure network foundation (VPC) for the Human Resource Management (HRM) System. Ensuring secure network infrastructure is a prerequisite for protecting sensitive HR data and complying with security regulations.

The HRM network architecture will be designed to include:

- **VPC (Virtual Private Cloud)**: An isolated network region on AWS.
- **Public Subnet**: For components that need to communicate directly with the Internet (e.g., Internet-facing Load Balancer, NAT Gateway, CloudFront/WAF Endpoints).
- **Private Subnet**: Dedicated to core resources requiring high security, not directly accessible from the Internet (e.g., EC2/Webapp Service, Amazon RDS for PostgreSQL, AWS ElastiCache, DynamoDB).
- **NAT Gateway**: Allows application servers (App Servers) in Private Subnets to access the Internet (e.g., to download security updates, pull Docker Images, or connect to AWS services outside the VPC) while keeping internal IP addresses hidden.
- **VPC Endpoint (PrivateLink)**: Establishes a private and secure connection between your VPC and other AWS services (such as Amazon S3, DynamoDB) without going through the Internet, enhancing security for uploading face check-in images.

![Network Architecture](/images/5-Workshop/5.3-S3-vpc/infrastructure.png)

#### 📝 Implementation Content

- [Initialize VPC & Subnet](5.3.1-create-gwe/)
- [Configure Internet & NAT Gateway](5.3.2-test-gwe/)
- [Configure Route Table](5.3.3-route-table/)
