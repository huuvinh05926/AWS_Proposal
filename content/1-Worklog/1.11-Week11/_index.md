---
title: "Week 11 Worklog"
date: "2025-11-11"
weight: 2
chapter: false
pre: " <b> 1.11. </b> "
---

### Week 11 Objectives:

- Understand attendance business logic (check-in/check-out rules)
- Integrate Lambda to automate attendance operations
- Develop Leave Management APIs

### Tasks to be carried out this week:

| Day | Learning / Research                                                                                 | Practice & Code                                                                                                                                                                                                                                        | AWS Event Attended                               |
| --- | --------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------ |
| 2   | - Learn check-in/check-out business rules <br> - Time calculation concepts                          | - Design database schema <br> - Prepare sample data                                                                                                                                                                                                    | Building Serverless Applications with AWS Lambda |
| 3   | - Learn about pagination <br> - Query with date range                                               | - Implement API: GET /api/v1/attendance <br> - Implement API: GET /api/v1/attendance/range                                                                                                                                                             |                                                  |
| 4   | - Learn about data update rules                                                                     | - Implement API: PUT /api/v1/attendance/{recordId}                                                                                                                                                                                                     |                                                  |
| 5   | - Learn about Lambda and API Gateway integration <br> - Trigger concepts (API Gateway, EventBridge) | - Create Lambda Function (Python/Node.js) <br> - Integrate with API Gateway                                                                                                                                                                            |                                                  |
| 6   | - Learn Lambda execution flow <br> - DynamoDB for event logging                                     | - Implement POST /api/attendance/start <br> - Implement POST /api/attendance/stop                                                                                                                                                                      |                                                  |
| 7   | - Learn leave management business logic <br> - Approval workflow (Pending, Approved, Rejected)      | - Implement API: GET /api/v1/leaves <br> - Implement API: GET /api/v1/leaves/history/{employeeId} <br> - Implement API: POST /api/v1/leaves <br> - Implement API: PUT /api/v1/leaves/{id}/approve <br> - Implement API: PUT /api/v1/leaves/{id}/reject |                                                  |

### Week 11 Achievements:

- Understood business rules for check-in/check-out: Automatic calculation of work hours, overtime, late arrival, early departure.

- Implemented 3 Attendance management APIs:

  - `GET /api/v1/attendance` (retrieve attendance list with pagination)
  - `GET /api/v1/attendance/range` (query by date range)
  - `PUT /api/v1/attendance/{recordId}` (update attendance record)

- Created Lambda Function (Python or Node.js), successfully integrated with API Gateway.

- Implemented 2 Lambda endpoints:

  - `POST /api/attendance/start` (start attendance via Lambda)
  - `POST /api/attendance/stop` (stop attendance via Lambda)

- Used DynamoDB to log Lambda execution events.

- Implemented 5 Leave Management APIs:

  - `GET /api/v1/leaves` (retrieve all leave requests)
  - `GET /api/v1/leaves/history/{employeeId}` (retrieve leave history by employee)
  - `POST /api/v1/leaves` (create new leave request)
  - `PUT /api/v1/leaves/{id}/approve` (approve leave request)
  - `PUT /api/v1/leaves/{id}/reject` (reject leave request)

- Implemented approval workflow with status: Pending → Approved/Rejected.

- Attended AWS online event: "Building Serverless Applications with AWS Lambda".

  - View EC2 service
  - Create and manage key pairs
  - Check information about running services
  - ...

- Acquired the ability to connect between the web interface and CLI to manage AWS resources in parallel.
- ...
