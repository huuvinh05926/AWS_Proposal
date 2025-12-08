---
title: "Worklog Tuần 10"
date: "2025-11-11"
weight: 2
chapter: false
pre: " <b> 1.10. </b> "
---

### Mục tiêu tuần 10:

- Triển khai Spring Data JPA & Repository để tương tác với Database.
- Xây dựng các API GET cho quản lý nhân viên (Employee).
- Phát triển API Thống kê/Lương (Payroll) và các API liên quan.

### Các công việc cần triển khai trong tuần này:

| Thứ | Nội dung Học/Research                                                                                   | Công việc Thực hành & Code                                                                              | AWS Event đã xem                       |
| --- | ------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------- | -------------------------------------- |
| 2   | Spring Data JPA & Repository: Tìm hiểu các lớp Repository để tương tác với Database (PostgreSQL/MySQL). | Cấu hình Spring Data JPA, tạo Entity classes và Repository interfaces.                                  | Deploying Java Applications on AWS EC2 |
| 3   | DTO Pattern & Exception Handling: Tìm hiểu pattern để xử lý dữ liệu và lỗi.                             | Triển khai API Employee: Xây dựng API GET /api/v1/employees và GET /api/v1/employees/total.             |                                        |
| 4   | RESTful API Best Practices: Thiết kế API chuẩn REST.                                                    | Hoàn thành các API: GET /api/v1/employees/active/count và GET /api/v1/employees/{id}.                   |                                        |
| 5   | Data Aggregation & Analysis: Phân tích yêu cầu Business Logic cho Payroll và các thống kê.              | Thiết kế database schema và business logic cho Payroll.                                                 |                                        |
| 6   | Java Stream API: Áp dụng để xử lý và tổng hợp dữ liệu phức tạp.                                         | Phát triển API Thống kê/Lương: Xây dựng API GET /api/v1/payroll/monthly và GET /api/v1/payroll/summary. |                                        |
| 7   | Task & Evaluation Management: Phân tích yêu cầu cho Tasks và Evaluations.                               | API Đánh giá & Task: Xây dựng cơ bản các API GET /api/v1/tasks và GET /api/v1/evaluations.              |                                        |

### Kết quả đạt được tuần 10:

- Hiểu rõ về **Spring Data JPA & Repository**:

  - Cấu hình Spring Data JPA với Database (PostgreSQL/MySQL)
  - Tạo Entity classes ánh xạ với database tables
  - Triển khai Repository interfaces cho các thao tác CRUD

- Thành công trong việc triển khai **API Employee**:

  - GET /api/v1/employees - Lấy danh sách nhân viên
  - GET /api/v1/employees/total - Tổng số nhân viên
  - GET /api/v1/employees/active/count - Số nhân viên đang hoạt động
  - GET /api/v1/employees/{id} - Lấy thông tin nhân viên theo ID

- Áp dụng **DTO Pattern & Exception Handling**:

  - Sử dụng DTO để transfer data giữa layers
  - Xử lý exceptions một cách nhất quán
  - Implement custom exception classes

- Nắm được **Data Aggregation & Analysis**:

  - Phân tích yêu cầu Business Logic cho Payroll
  - Thiết kế database schema phù hợp
  - Xác định các thống kê cần thiết

- Phát triển thành công **API Thống kê/Lương**:

  - GET /api/v1/payroll/monthly - Báo cáo lương hàng tháng
  - GET /api/v1/payroll/summary - Tổng hợp thống kê lương

- Áp dụng **Java Stream API**:

  - Xử lý và filter dữ liệu phức tạp
  - Tổng hợp và group data
  - Optimize performance với parallel streams

- Xây dựng **API Đánh giá & Task**:

  - GET /api/v1/tasks - Lấy danh sách công việc
  - GET /api/v1/evaluations - Lấy danh sách đánh giá
  - Thiết lập relationships giữa các entities

- Tham gia AWS Event:
  - Deploying Java Applications on AWS EC2 - Áp dụng lý thuyết EC2 cho việc triển khai ứng dụng Java
