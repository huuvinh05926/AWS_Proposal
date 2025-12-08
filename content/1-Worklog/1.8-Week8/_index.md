---
title: "Week 8 Worklog"
date: "2025-11-11"
weight: 1
chapter: false
pre: " <b> 1.8. </b> "
---

### Week 8 Objectives:

- Understand CloudFront CDN and its benefits
- Set up Route 53 to manage domain names
- Learn and configure AWS WAF to protect web applications

### Tasks to be carried out this week:

| Day | Learning / Research                                                                                         | Practice & Code                                                                 | AWS Event Attended                            |
| --- | ----------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------- | --------------------------------------------- |
| 2   | - Learn CloudFront CDN concepts <br> - CloudFront Distribution types <br> - Origin concept (S3, HTTP/HTTPS) | - Create CloudFront Distribution <br> - Configure Origin pointing to S3 Bucket  | Optimizing Performance with Amazon CloudFront |
| 3   | - Learn about Cache Policy <br> - Origin Access Control (OAC)                                               | - Configure OAC for S3 <br> - Integrate S3 with CloudFront                      |                                               |
| 4   | - TTL (Time to Live) concepts <br> - CORS concepts                                                          | - Test with TTL=300 <br> - Configure CORS headers                               |                                               |
| 5   | - Learn about Route 53 and DNS <br> - Hosted Zone concepts                                                  | - Create Hosted Zone <br> - Update Nameserver with domain provider              |                                               |
| 6   | - Learn about DNS record types <br> - A Record, CNAME concepts                                              | - Create A record pointing to CloudFront                                        |                                               |
| 7   | - Learn about AWS WAF and OWASP Top 10 <br> - Rate Limit concepts                                           | - Create WebACL <br> - Configure basic rules <br> - Attach WebACL to CloudFront | AWS Networking Fundamentals                   |

### Week 8 Achievements:

- Created CloudFront Distribution, successfully integrated with S3 Bucket via OAC (Origin Access Control).

- Configured Cache Policy and TTL=300, verified content cached at CloudFront Edge Location.

- Successfully configured CORS to allow cross-origin requests from JavaScript.

- Created Hosted Zone on Route 53, updated Nameserver with the domain provider (e.g., GoDaddy).

- Created A record pointing to CloudFront Distribution, verified domain successfully resolves to the CloudFront endpoint.

- Created WebACL on AWS WAF, configured basic rules against OWASP Top 10 (e.g., SQL Injection, XSS), and Rate Limit (e.g., 2000 requests/5 minutes).

- Successfully integrated WebACL with CloudFront Distribution, verified requests are checked and blocked when violating rules.

- Attended AWS online events: "Optimizing Performance with Amazon CloudFront" and "AWS Networking Fundamentals".

  - View EC2 service
  - Create and manage key pairs
  - Check information about running services
  - ...

- Acquired the ability to connect between the web interface and CLI to manage AWS resources in parallel.
- ...
