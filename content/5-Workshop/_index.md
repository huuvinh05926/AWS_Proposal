---
title: "Workshop"
date: "2025-11-11"
weight: 5
chapter: false
pre: " <b> 5. </b> "
---

<!-- {{% notice warning %}}
⚠️ **Note:** The information below is for reference purposes only. Please **do not copy verbatim** for your report, including this warning.
{{% /notice %}} -->

# Deploy Human Resource Management System on AWS Cloud

#### Overview

This workshop demonstrates a comprehensive **Cloud Migration** journey, showcasing how to migrate and deploy a **Human Resource Management (HRM) System** from on-premises infrastructure to **AWS Cloud** using modern **Cloud-Native** architecture patterns.

The HRM system is a core platform built on **Java Spring Boot**, designed to comprehensively manage employee records, attendance tracking, and other HR tasks. This workshop focuses on migrating the application from an on-premise environment to a **Cloud-Native architecture** on AWS, with particular emphasis on ensuring **sensitive data security** and **scalability**.

The migration strictly adheres to the pillars of the **AWS Well-Architected Framework**: **Security**, **Reliability**, **Performance Efficiency**, and **Cost Optimization**.

#### Solution Architecture Overview

The HRM project uses a Microservices architecture and carefully selected AWS services to maximize security for sensitive HR data.

**Architecture Components:**

- **Compute & Logic Layer:**

  - **AWS Elastic Beanstalk (or ECS):** Leverages the **Docker** platform to package and deploy **Java Spring Boot** applications. This simplifies infrastructure management and automates **Auto Scaling** and Elastic Load Balancing.
  - **AWS Lambda & API Gateway:** Used to process asynchronous tasks (e.g., report generation, salary calculation) or lightweight APIs, optimizing costs and performance.

- **Data & Persistence Layer:**

  - **Amazon RDS for PostgreSQL:** Used as the primary relational database (RDB) to store employee records, salary information, and sensitive data. Placed in **Private Subnet** to maintain the highest security.
  - **Amazon DynamoDB:** Used for unstructured, high-speed data (e.g., storing record change history, transaction logs).
  - **Amazon S3:** Used to store and distribute static assets such as **profile pictures** and **face check-in images** with superior durability.

- **Security & Authentication:**

  - **Amazon Cognito:** Provides user identity management services, ensuring authentication and access authorization for employees and management.
  - **AWS Secrets Manager:** Integrated to securely store and manage API keys, database credentials, and **Tokens** for session creation or external integration.

- **DevOps & Monitoring:**
  - **AWS CodePipeline & CodeBuild:** Automates the CI/CD (Continuous Integration/Continuous Deployment) process from source code to production environment.
  - **Amazon CloudWatch & SNS:** Monitors system health and sends alerts when issues occur.

#### Workshop Objectives

By completing this workshop, you will:

1. Build secure network infrastructure with VPC, Subnets, and Security Groups
2. Deploy data layer with RDS PostgreSQL and ElastiCache Redis in Private Subnets
3. Containerize and deploy Java Spring Boot application using Docker and Elastic Beanstalk
4. Implement automated CI/CD pipeline with CodeBuild and CodePipeline
5. Optimize performance using CloudFront CDN and S3 for static assets
6. Enhance security with AWS WAF to protect against common web attacks
7. Set up monitoring and alerting with CloudWatch and SNS
8. Learn proper resource cleanup procedures to avoid unexpected costs

#### Content

1. [Introduction to HRM System](5.1-Workshop-overview/)
2. [Prerequisites](5.2-Prerequiste/)
3. [Setup Network Infrastructure](5.3-S3-vpc/)
4. [Deploy Data Layer](5.4-S3-onprem/)
5. [Deploy Application](5.5-Policy/)
6. [Automate CI/CD](5.6-Cleanup/)
7. [Optimization & Security](5.7-Section7/)
8. [Monitoring & Operations](5.8-Section8/)
9. [Clean up Resources](5.9-Section9/)
