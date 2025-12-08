---
title: "Worklog Tuần 9"
date: "2025-11-11"
weight: 1
chapter: false
pre: " <b> 1.9. </b> "
---

### Mục tiêu tuần 9:

- Tìm hiểu API Gateway: Các loại API (REST/HTTP), cách hoạt động của Stage và Resource.
- Học về Cognito User Pool: Quản lý người dùng và xác thực JWT.
- Hiểu cơ chế Authorizer trong API Gateway.

### Các công việc cần triển khai trong tuần này:

| Thứ | Nội dung Học/Research                                                          | Công việc Thực hành & Code                                                                                                                 | AWS Event đã xem                             |
| --- | ------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------ | -------------------------------------------- |
| 2   | API Gateway Overview: Tìm hiểu các loại API (REST/HTTP), khái niệm cơ bản.     | Khởi tạo API Gateway (HTTP API) cơ bản, làm quen với giao diện.                                                                            | Modern API Development with API Gateway      |
| 3   | API Gateway Advanced: Stage, Resource, Method, và cách hoạt động.              | Tạo API Gateway: Định nghĩa routes base cho HR System: /api/v1/employees.                                                                  |                                              |
| 4   | API Gateway Routes: Thiết kế RESTful API cho hệ thống.                         | Định nghĩa thêm routes: /api/v1/attendance, /api/v1/payroll.                                                                               |                                              |
| 5   | Cognito User Pool: Cơ chế quản lý người dùng, App Client.                      | Setup Cognito: Tạo Cognito User Pool và App Client.                                                                                        | Secure Your Applications with Amazon Cognito |
| 6   | Cognito Authentication: Các luồng xác thực và JSON Web Token (JWT).            | Cấu hình các luồng xác thực trong Cognito User Pool.                                                                                       |                                              |
| 7   | Cognito Authorizer: Cơ chế hoạt động của Cognito Authorizer trong API Gateway. | Kiểm thử JWT: Cấu hình Cognito Authorizer cho một route thử nghiệm. Dùng Hosted UI để lấy JWT và kiểm tra quyền truy cập API bằng Postman. |                                              |

### Kết quả đạt được tuần 9:

- Hiểu rõ về **Amazon API Gateway**:

  - Phân biệt các loại API (REST API vs HTTP API)
  - Nắm được khái niệm Stage, Resource, Method
  - Hiểu cách hoạt động của routing và integration

- Thành công trong việc tạo API Gateway:

  - Khởi tạo HTTP API cho HR System
  - Định nghĩa các routes base:
    - /api/v1/employees
    - /api/v1/attendance
    - /api/v1/payroll
  - Cấu hình Stage và deployment

- Nắm được **Amazon Cognito User Pool**:

  - Cơ chế quản lý người dùng
  - App Client và cách tạo JWT
  - Các luồng xác thực (Authorization Code, Implicit, etc.)

- Setup Cognito thành công:

  - Tạo Cognito User Pool
  - Cấu hình App Client
  - Thiết lập các luồng xác thực phù hợp

- Hiểu về **Cognito Authorizer**:

  - Cơ chế hoạt động của Authorizer trong API Gateway
  - Cách validate JWT token
  - Flow xác thực từ client đến backend

- Kiểm thử JWT thành công:

  - Cấu hình Cognito Authorizer cho route thử nghiệm
  - Sử dụng Hosted UI để lấy JWT token
  - Kiểm tra quyền truy cập API bằng Postman với JWT

- Tham gia các AWS Events:
  - Modern API Development with API Gateway
  - Secure Your Applications with Amazon Cognito
