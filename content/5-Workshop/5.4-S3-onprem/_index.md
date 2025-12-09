---
title: "Deploy Data Layer"
date: "2025-11-11"
weight: 4
chapter: false
pre: " <b> 5.4. </b> "
---

#### Overview

Data is the most important asset of any system. Therefore, we will set up the Data Layer for MiniMarket with the criteria: **Maximum Security** and **High Performance**.

We will deploy two core services:

- **Amazon RDS (Relational Database Service)**: Using SQL Server to store business data (Products, Orders, Users). The database will be placed in a Private Subnet to prevent direct access from the Internet.
- **Amazon ElastiCache (Redis)**: Using Redis as an in-memory cache to store login sessions and reduce query load on the main database.

![Data Layer Architecture](/images/5-Workshop/5.4-S3-onprem/data-diagram.png)

#### Content

- [Setup Security Groups for DB & Cache](5.4.1-prepare/)
- [Initialize Amazon RDS (SQL Server)](5.4.2-create-interface-enpoint/)
- [Initialize Amazon ElastiCache (Redis)](5.4.3-test-endpoint/)
