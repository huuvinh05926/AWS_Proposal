---
title: "Giới thiệu"
date: "2025-11-11"
weight: 1
chapter: false
pre: " <b> 5.1. </b> "
---

#### Giới thiệu Hệ thống Quản lý Nhân sự (Human Resource Management - HRM)

Hệ thống HRM là nền tảng cốt lõi được phát triển trên **Java Spring Boot**, được thiết kế để quản lý toàn diện hồ sơ nhân viên, quy trình chấm công, và các tác vụ nhân sự khác. Workshop này tập trung vào việc di chuyển ứng dụng từ môi trường On-premise lên **kiến trúc Cloud-Native** trên AWS, đặc biệt chú trọng vào việc đảm bảo **bảo mật dữ liệu nhạy cảm** và **khả năng mở rộng (Scalability)**.

Việc di chuyển này tuân thủ nghiêm ngặt các trụ cột của **AWS Well-Architected Framework**: **Security** (Bảo mật), **Reliability** (Độ tin cậy), **Performance Efficiency** (Hiệu suất), và **Cost Optimization** (Tối ưu chi phí).

#### Tổng quan Kiến trúc Giải pháp trên AWS

Dự án HRM sử dụng kiến trúc Microservices và các dịch vụ AWS được lựa chọn nhằm tối đa hóa bảo mật cho dữ liệu nhân sự nhạy cảm.

**Kiến trúc giải pháp:**

- **Compute & Logic Layer (Tầng Tính toán & Logic):**
  - **AWS Elastic Beanstalk (hoặc ECS):** Tận dụng nền tảng **Docker** để đóng gói và triển khai ứng dụng **Java Spring Boot**. Điều này đơn giản hóa quy trình quản trị hạ tầng, tự động hóa khả năng **Auto Scaling** và cân bằng tải (Elastic Load Balancing).
  - **AWS Lambda & API Gateway:** Sử dụng để xử lý các nghiệp vụ phi đồng bộ (ví dụ: tạo báo cáo, tính toán lương) hoặc các API nhẹ, tối ưu chi phí và hiệu suất.
- **Data & Persistence Layer (Tầng Dữ liệu & Lưu trữ):**
  - **Amazon RDS for PostgreSQL:** Được sử dụng làm cơ sở dữ liệu quan hệ chính (RDB) để lưu trữ hồ sơ nhân viên, thông tin lương, và dữ liệu nhạy cảm. Được đặt trong **Private Subnet** để duy trì tính bảo mật cao nhất.
  - **Amazon DynamoDB:** Được sử dụng cho dữ liệu phi cấu trúc, tốc độ cao (ví dụ: lưu trữ lịch sử thay đổi hồ sơ, nhật ký giao dịch).
  - **Amazon S3:** Được sử dụng để lưu trữ và phân phối tài nguyên tĩnh như **ảnh đại diện** và **ảnh check-in khuôn mặt** với độ bền vượt trội.
- **Security & Authentication (Bảo mật & Xác thực):**
  - **Amazon Cognito:** Cung cấp dịch vụ quản lý danh tính người dùng, đảm bảo việc xác thực và ủy quyền truy cập cho nhân viên và quản lý.
  - **AWS Secrets Manager:** Được tích hợp để lưu trữ và quản lý an toàn các khóa API, thông tin đăng nhập database, và các **Token** phục vụ cho việc tạo session hoặc tích hợp bên ngoài.
  - **AWS WAF & Amazon CloudFront:** Cung cấp lớp bảo vệ ứng dụng khỏi các mối đe dọa web (OWASP Top 10) và phân phối nội dung toàn cầu an toàn.
- **DevOps & Monitoring (Vận hành & Giám sát):**
  _ **AWS CodePipeline & CodeBuild:** Tự động hóa quy trình **CI/CD** từ kho chứa mã nguồn (GitHub) đến môi trường AWS, đảm bảo việc triển khai nhanh chóng và đáng tin cậy.
  _ **Amazon CloudWatch & AWS SNS:** Theo dõi các chỉ số hệ thống (CPU, Network, Độ trễ) và cấu hình cảnh báo thông báo theo thời gian thực (qua SNS) để đảm bảo độ tin cậy của dịch vụ. \*
  ![overview](/images/2-Proposal/proposalaws1.jpg)
