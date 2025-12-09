---
title: "Introduction"
date: "2025-11-11"
weight: 1
chapter: false
pre: " <b> 5.1. </b> "
---

#### Introduction to Human Resource Management (HRM) System

The HRM system is a core platform developed on **Java Spring Boot**, designed to comprehensively manage employee records, attendance processes, and other HR tasks. This workshop focuses on migrating the application from an On-premise environment to a **Cloud-Native architecture** on AWS, with particular emphasis on ensuring **sensitive data security** and **scalability**.

This migration strictly adheres to the pillars of the **AWS Well-Architected Framework**: **Security**, **Reliability**, **Performance Efficiency**, and **Cost Optimization**.

#### Solution Architecture Overview on AWS

The HRM project utilizes a Microservices architecture and carefully selected AWS services to maximize security for sensitive HR data.

**Solution Architecture:**

- **Compute & Logic Layer:**
  - **AWS Elastic Beanstalk (or ECS):** Leverages the **Docker** platform to package and deploy the **Java Spring Boot** application. This simplifies infrastructure management, automates **Auto Scaling**, and provides Elastic Load Balancing.
  - **AWS Lambda & API Gateway:** Used to handle asynchronous operations (e.g., report generation, salary calculations) or lightweight APIs, optimizing cost and performance.
- **Data & Persistence Layer:**
  - **Amazon RDS for PostgreSQL:** Serves as the primary relational database (RDB) for storing employee records, salary information, and sensitive data. Placed in a **Private Subnet** to maintain the highest level of security.
  - **Amazon DynamoDB:** Used for unstructured, high-speed data (e.g., storing record change history, transaction logs).
  - **Amazon S3:** Used to store and distribute static resources such as **profile pictures** and **face check-in images** with superior durability.
- **Security & Authentication:**
  - **Amazon Cognito:** Provides user identity management services, ensuring authentication and access authorization for employees and managers.
  - **AWS Secrets Manager:** Integrated to securely store and manage API keys, database credentials, and **Tokens** for session creation or external integrations.
  - **AWS WAF & Amazon CloudFront:** Provides application protection against web threats (OWASP Top 10) and secure global content distribution.
- **DevOps & Monitoring:**
  - **AWS CodePipeline & CodeBuild:** Automates the **CI/CD** process from source code repository (GitHub) to AWS environment, ensuring fast and reliable deployment.
  - **Amazon CloudWatch & AWS SNS:** Monitors system metrics (CPU, Network, Latency) and configures real-time alert notifications (via SNS) to ensure service reliability.

![overview](/images/2-Proposal/proposalaws1.jpg)
