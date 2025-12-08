---
title: "Translated Blogs"
date: "2025-11-11"
weight: 3
chapter: false
pre: " <b> 3. </b> "
---

This section will list and introduce the blogs you have translated. For example:

### [Blog 1 - Automating Budget Management Across Multi-Account Environments](3.1-Blog1/)

This blog demonstrates how to automate budget management across multiple AWS accounts using an event-driven architecture. The solution enables centralized budget management with automated email notifications, allowing organizations to set and enforce account-specific budgets from a central management account. Key technologies include Amazon DynamoDB for storing budget values, AWS Lambda for propagating budget configurations via AWS Systems Manager Parameter Store, and AWS Budgets for real-time spending monitoring. The article provides detailed deployment steps using CloudFormation templates and explains how to handle budget alert states and implement future enhancements like AWS Budget Actions and ServiceNow integration for automated cost optimization.

### [Blog 2 - Guidance for a media lake on AWS](3.2-Blog2/)

This blog introduces a comprehensive solution for building a centralized media lake on AWS to manage large volumes of digital media files scattered across multiple Amazon S3 buckets. The guidance provides a reference architecture that creates a unified search interface, allowing users to search media files across all S3 locations simultaneously. It features automated event-driven media processing pipelines using a drag-and-drop interface, AI-powered natural language search capabilities, and seamless integration with AWS services. The solution can be deployed via three methods: AWS CloudFormation template, local deployment using AWS CDK, or integration with existing CI/CD pipelines, making it flexible for different organizational needs.

### [Blog 3 - Dynamic configuration updates in .NET using Parameter Store and Secrets Manager](3.3-Blog3/)

This blog explores an advanced approach to managing configuration and secrets in .NET applications using AWS Systems Manager Parameter Store and AWS Secrets Manager. The solution demonstrates how to reference Secrets Manager secrets through Parameter Store using the `/aws/reference/secretsmanager/` format, enabling unified access to both configuration and sensitive data. Key features include implementing dynamic configuration reloading without application restarts using the IOptionsMonitor pattern, environment separation through hierarchical Parameter Store structures, and secure storage with proper encryption and access controls. The article provides step-by-step C# code examples showing how to set up extension methods, configuration models, and dependency injection for seamless integration with .NET 8 applications.
