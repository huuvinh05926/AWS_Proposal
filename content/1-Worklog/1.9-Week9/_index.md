---
title: "Week 9 Worklog"
date: "2025-11-11"
weight: 1
chapter: false
pre: " <b> 1.9. </b> "
---

### Week 9 Objectives:

- Understand API Gateway types (REST API vs HTTP API)
- Set up Cognito User Pool for user management
- Integrate JWT authentication from Cognito into API Gateway

### Tasks to be carried out this week:

| Day | Learning / Research                                                                          | Practice & Code                                                                 | AWS Event Attended                             |
| --- | -------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------- | ---------------------------------------------- |
| 2   | - Learn about API Gateway <br> - REST API vs HTTP API <br> - Routes and Integration concepts | - Create HTTP API <br> - Configure basic settings                               | Modern API Development with Amazon API Gateway |
| 3   | - Learn routing structure <br> - HTTP Methods: GET, POST, PUT, DELETE                        | - Create routes for /api/v1/employees                                           |                                                |
| 4   | - Learn about complex routing                                                                | - Create routes for /api/v1/attendance <br> - Create routes for /api/v1/payroll |                                                |
| 5   | - Learn about Cognito User Pool <br> - User Pool vs Identity Pool <br> - App Client concepts | - Create Cognito User Pool <br> - Configure App Client                          |                                                |
| 6   | - Learn about JWT Token (id_token, access_token) <br> - JWT authentication flows             | - Test login and retrieve JWT from Cognito                                      |                                                |
| 7   | - Learn about Authorizers <br> - Cognito Authorizer configuration                            | - Configure Cognito Authorizer in API Gateway <br> - Test with Postman          | Secure Your Applications with Amazon Cognito   |

### Week 9 Achievements:

- Created HTTP API on API Gateway, clearly understood the differences between REST API and HTTP API (cost, latency, features).

- Successfully configured routes for the HR System:

  - `/api/v1/employees` (GET, POST, PUT, DELETE)
  - `/api/v1/attendance` (GET, POST, PUT)
  - `/api/v1/payroll` (GET)

- Created Cognito User Pool, configured App Client with appropriate settings (e.g., Allow username/password, Enable refresh token).

- Successfully tested login flow, retrieved JWT Token (id_token, access_token) from Cognito.

- Configured Cognito Authorizer in API Gateway, integrated JWT authentication.

- Used Postman to test APIs with JWT Token in the Authorization header, verified that requests without a token are rejected with HTTP 401.

- Attended AWS online events: "Modern API Development with Amazon API Gateway" and "Secure Your Applications with Amazon Cognito".

  - View EC2 service
  - Create and manage key pairs
  - Check information about running services
  - ...

- Acquired the ability to connect between the web interface and CLI to manage AWS resources in parallel.
- ...
