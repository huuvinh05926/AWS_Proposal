---
title: "Week 10 Worklog"
date: "2025-11-11"
weight: 2
chapter: false
pre: " <b> 1.10. </b> "
---

### Week 10 Objectives:

- Configure Spring Data JPA and connect to database (PostgreSQL/MySQL)
- Develop Employee management APIs
- Develop Payroll statistics APIs

### Tasks to be carried out this week:

| Day | Learning / Research                                               | Practice & Code                                                                                      | AWS Event Attended                     |
| --- | ----------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------- | -------------------------------------- |
| 2   | - Learn Spring Data JPA <br> - Entity and Repository concepts     | - Configure application.properties <br> - Create Entity classes <br> - Create Repository interfaces  | Deploying Java Applications on AWS EC2 |
| 3   | - Learn about DTO Pattern <br> - Separation of Entity and DTO     | - Implement API: GET /api/v1/employees <br> - Implement API: GET /api/v1/employees/total             |                                        |
| 4   | - Learn about JPA Query Methods                                   | - Implement API: GET /api/v1/employees/active/count <br> - Implement API: GET /api/v1/employees/{id} |                                        |
| 5   | - Learn payroll business logic <br> - Database schema for payroll | - Design payroll tables <br> - Prepare sample data                                                   |                                        |
| 6   | - Learn Java Stream API <br> - groupingBy, summingDouble          | - Implement API: GET /api/v1/payroll/monthly <br> - Implement API: GET /api/v1/payroll/summary       |                                        |
| 7   | - Learn about task/evaluation business logic                      | - Implement API: GET /api/v1/tasks <br> - Implement API: GET /api/v1/evaluations                     |                                        |

### Week 10 Achievements:

- Successfully configured Spring Data JPA, connected to PostgreSQL/MySQL database.

- Created Entity classes (Employee, Payroll, Task, Evaluation) corresponding to database tables.

- Created Repository interfaces extending JpaRepository, understood built-in methods (findAll, findById, save, delete).

- Implemented 4 Employee management APIs:

  - `GET /api/v1/employees` (retrieve all employees)
  - `GET /api/v1/employees/total` (count total employees)
  - `GET /api/v1/employees/active/count` (count active employees)
  - `GET /api/v1/employees/{id}` (retrieve employee by ID)

- Implemented 2 Payroll statistics APIs:

  - `GET /api/v1/payroll/monthly` (retrieve monthly payroll list)
  - `GET /api/v1/payroll/summary` (retrieve total statistics by department)

- Implemented 2 additional APIs:

  - `GET /api/v1/tasks` (retrieve task list)
  - `GET /api/v1/evaluations` (retrieve evaluation list)

- Used Java Stream API to process data, group, and calculate statistics efficiently.

- Attended AWS online event: "Deploying Java Applications on AWS EC2".

  - View EC2 service
  - Create and manage key pairs
  - Check information about running services
  - ...

- Acquired the ability to connect between the web interface and CLI to manage AWS resources in parallel.
- ...
