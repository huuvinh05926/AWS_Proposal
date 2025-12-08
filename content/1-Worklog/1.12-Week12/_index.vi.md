---
title: "Worklog Tuần 12"
date: "2025-11-11"
weight: 2
chapter: false
pre: " <b> 1.12 </b> "
---

### Mục tiêu tuần 12:

- Tối ưu hóa hiệu năng với ElastiCache (Redis) và bảo mật với Secrets Manager.
- Tích hợp Face Recognition và xây dựng Module Hỗ trợ.
- Hoàn thiện tài liệu API và kiểm tra bảo mật.

### Các công việc cần triển khai trong tuần này:

| Thứ | Nội dung Học/Research                                                                   | Công việc Thực hành & Code                                                                                                              | AWS Event đã xem                                          |
| --- | --------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------- |
| 2   | ElastiCache (Redis): Cache Architecture và Caching Strategy.                            | Tối ưu hóa: Setup Redis Cache cho ứng dụng.                                                                                             | Improving Application Performance with Amazon ElastiCache |
| 3   | Caching Implementation: Best practices cho caching data.                                | Tối ưu API thống kê lương (/payroll/summary) bằng Redis caching.                                                                        |                                                           |
| 4   | AWS Secrets Manager: Bảo mật thông tin kết nối Database và API keys.                    | Lưu trữ mật khẩu DB/API vào Secrets Manager, cập nhật application configuration.                                                        |                                                           |
| 5   | Feature Tích hợp: Phân tích yêu cầu Tích hợp Face Recognition và Module Hỗ trợ.         | API Tích hợp & Hỗ trợ: Xây dựng GET /api/v1/evaluations/{id} và POST /api/v1/evaluations.                                               | AI/ML on AWS – Image & Face Recognition Basics            |
| 6   | Support Ticket System: Thiết kế workflow xử lý ticket và notification.                  | Triển khai GET /api/v1/support-tickets, PUT /api/v1/support-tickets/{id}/forward, PUT /api/v1/support-tickets/{id}/notify.              |                                                           |
| 7   | API Documentation & Security Review: Swagger/OpenAPI và Spring Security best practices. | Hoàn thiện: Cập nhật API Documentation (Swagger/OpenAPI) cho tất cả endpoints. Kiểm tra lại Spring Security/JWT cho các API quan trọng. |                                                           |

### Kết quả đạt được tuần 12:

- Hiểu rõ về **ElastiCache (Redis)**:

  - Cache Architecture và design patterns
  - Caching Strategy (Cache-Aside, Write-Through, Write-Behind)
  - Redis data structures và use cases

- Thành công trong việc **Tối ưu hóa hiệu năng**:

  - Setup Redis Cache cluster
  - Implement caching cho API /payroll/summary
  - Giảm đáng kể response time và database load

- Nắm được **AWS Secrets Manager**:

  - Bảo mật thông tin nhạy cảm (DB credentials, API keys)
  - Rotation policy cho secrets
  - Integration với Spring Boot application

- Triển khai **Secrets Management**:

  - Lưu trữ mật khẩu DB/API vào Secrets Manager
  - Cập nhật application configuration
  - Remove hardcoded credentials

- Xây dựng thành công **API Tích hợp & Hỗ trợ**:

  - GET /api/v1/evaluations/{id} - Lấy chi tiết đánh giá
  - POST /api/v1/evaluations - Tạo đánh giá mới
  - GET /api/v1/support-tickets - Danh sách ticket hỗ trợ
  - PUT /api/v1/support-tickets/{id}/forward - Chuyển tiếp ticket
  - PUT /api/v1/support-tickets/{id}/notify - Gửi thông báo

- Tích hợp **Face Recognition**:

  - Phân tích yêu cầu tích hợp AI/ML
  - Thiết kế workflow cho face recognition
  - Chuẩn bị integration với AWS Rekognition

- Hoàn thiện **API Documentation**:

  - Cập nhật Swagger/OpenAPI specification
  - Document tất cả endpoints với examples
  - Generate interactive API documentation

- Kiểm tra **Spring Security/JWT**:

  - Review authentication và authorization flow
  - Audit các API endpoints quan trọng
  - Fix security vulnerabilities

- Tham gia các AWS Events:
  - Improving Application Performance with Amazon ElastiCache
  - AI/ML on AWS – Image & Face Recognition Basics
