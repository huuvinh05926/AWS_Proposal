---
title: "Monitoring & Operations"
date: "2025-11-11"
weight: 8
chapter: false
pre: " <b> 5.8. </b> "
---

#### Monitoring & Operations

#### Overview

A Production system cannot be considered complete without **Monitoring** and **Alerting** capabilities. You cannot sit and watch the screen 24/7 to check if the Server is still alive.

In this module, we will set up monitoring and alerting for the MiniMarket system using AWS operational management services:

- **Amazon CloudWatch**: Collect metrics from EC2, RDS, ELB
- **Amazon SNS (Simple Notification Service)**: Notification delivery service. We will use it to send emails to administrators when the system encounters issues

We will set up a **CloudWatch Alarm** to monitor the Web Server's CPU. If CPU exceeds 70% (a sign of overload or attack), the system will automatically trigger SNS to send an emergency alert email.

![Monitoring Architecture](/images/5-Workshop/5.8-Section8/monitoring-diagram.png)

#### Content

- [Setup CloudWatch & SNS Alerts](5.8.1-subsection1/)
