---
title: "Week 12 Worklog"
date: "2025-11-11"
weight: 2
chapter: false
pre: " <b> 1.12. </b> "
---

### Week 12 Objectives:

- Use ElastiCache (Redis) to improve API performance
- Integrate AWS Secrets Manager for credentials security
- Develop APIs related to evaluations and support system

### Tasks to be carried out this week:

| Day | Learning / Research                                                | Practice & Code                                                                                                                                                                                                                                               | AWS Event Attended                                        |
| --- | ------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------- |
| 2   | - Learn about ElastiCache (Redis) <br> - Cache-Aside Pattern       | - Create Redis Cluster <br> - Configure Security Group                                                                                                                                                                                                        | Improving Application Performance with Amazon ElastiCache |
| 3   | - Learn Spring Data Redis <br> - RedisTemplate and CacheManager    | - Integrate Redis into Spring Boot <br> - Implement caching for /payroll/summary API                                                                                                                                                                          |                                                           |
| 4   | - Learn AWS Secrets Manager <br> - Environment variable management | - Store DB credentials in Secrets Manager <br> - Update application.properties to retrieve secrets                                                                                                                                                            |                                                           |
| 5   | - Learn about Amazon Rekognition <br> - Face Recognition APIs      | - Analyze Rekognition Face Recognition <br> - Prepare employee photos                                                                                                                                                                                         | AI/ML on AWS – Image & Face Recognition Basics            |
| 6   | - Learn business logic for evaluations and support tickets         | - Implement API: GET /api/v1/evaluations/{id} <br> - Implement API: POST /api/v1/evaluations                                                                                                                                                                  |                                                           |
| 7   | - Complete support system APIs <br> - Swagger documentation        | - Implement API: GET /api/v1/support-tickets <br> - Implement API: PUT /api/v1/support-tickets/{id}/forward <br> - Implement API: PUT /api/v1/support-tickets/{id}/notify <br> - Generate Swagger/OpenAPI documentation <br> - Review Spring Security and JWT |                                                           |

### Week 12 Achievements:

- Created ElastiCache Redis Cluster, configured Security Group to allow connections from Spring Boot application.

- Integrated Spring Data Redis, implemented Cache-Aside Pattern to cache data from `/payroll/summary` API, significantly improving response time.

- Stored database credentials and API keys in AWS Secrets Manager, updated `application.properties` to automatically retrieve credentials via AWS SDK.

- Analyzed Amazon Rekognition APIs for Face Recognition, prepared employee face photos for future features (e.g., face recognition attendance).

- Implemented 2 Evaluation management APIs:

  - `GET /api/v1/evaluations/{id}` (retrieve evaluation by ID)
  - `POST /api/v1/evaluations` (create new evaluation)

- Implemented 3 Support System APIs:

  - `GET /api/v1/support-tickets` (retrieve support ticket list)
  - `PUT /api/v1/support-tickets/{id}/forward` (forward ticket to relevant department)
  - `PUT /api/v1/support-tickets/{id}/notify` (send notification to employee)

- Generated complete API documentation using Swagger/OpenAPI, including all endpoints (Employee, Payroll, Attendance, Leave, Evaluation, Support).

- Reviewed the entire Spring Security and JWT authentication system, ensuring all APIs are properly secured.

- Attended AWS online events: "Improving Application Performance with Amazon ElastiCache" and "AI/ML on AWS – Image & Face Recognition Basics".

  - View EC2 service
  - Create and manage key pairs
  - Check information about running services
  - ...

- Acquired the ability to connect between the web interface and CLI to manage AWS resources in parallel.
- ...
