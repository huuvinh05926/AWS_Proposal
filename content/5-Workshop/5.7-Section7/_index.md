---
title: "Optimization & Security"
date: "2025-11-11"
weight: 7
chapter: false
pre: " <b> 5.7. </b> "
---

#### Optimization & Security

#### Overview

A Production system needs not only to "run" but also to "run fast" and "securely". In this section, we will fine-tune the MiniMarket architecture to achieve higher performance and enhanced security.

#### Implementation items:

- **Offloading Static Assets**: Transfer all product images from Web Server to Amazon S3 and distribute via Amazon CloudFront (CDN) to increase global page load speed and reduce server load
- **Security Hardening**: Deploy AWS WAF (Web Application Firewall) in front of CloudFront to protect the application from common attacks such as SQL Injection and XSS

![Security Architecture](/images/5-Workshop/5.7-Img/security-diagram.png)

#### Content

- [Configure S3 and CloudFront](5.7.1-subsection1/)
- [Setup AWS WAF](5.7.2-subsection2/)
