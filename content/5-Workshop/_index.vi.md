---
title: "Workshop"
date: "2025-11-11"
weight: 5
chapter: false
pre: " <b> 5. </b> "
---

<!-- {{% notice warning %}}
⚠️ **Lưu ý:** Các thông tin dưới đây chỉ nhằm mục đích tham khảo, vui lòng **không sao chép nguyên văn** cho bài báo cáo của bạn kể cả warning này.
{{% /notice %}} -->

# Triển khai Hệ thống Quản lý Nhân sự trên AWS Cloud

#### Tổng quan

Workshop này trình bày hành trình **Di chuyển lên Cloud** toàn diện, giới thiệu cách di chuyển và triển khai **Hệ thống Quản lý Nhân sự (HRM)** từ hạ tầng on-premises lên **AWS Cloud** sử dụng các mẫu kiến trúc **Cloud-Native** hiện đại.

Hệ thống HRM là nền tảng cốt lõi được phát triển trên **Java Spring Boot**, được thiết kế để quản lý toàn diện hồ sơ nhân viên, quy trình chấm công, và các tác vụ nhân sự khác. Workshop này tập trung vào việc di chuyển ứng dụng từ môi trường on-premise lên **kiến trúc Cloud-Native** trên AWS, đặc biệt chú trọng vào việc đảm bảo **bảo mật dữ liệu nhạy cảm** và **khả năng mở rộng (Scalability)**.

Việc di chuyển này tuân thủ nghiêm ngặt các trụ cột của **AWS Well-Architected Framework**: **Security** (Bảo mật), **Reliability** (Độ tin cậy), **Performance Efficiency** (Hiệu suất), và **Cost Optimization** (Tối ưu chi phí).

#### Tổng quan Kiến trúc Giải pháp

Dự án HRM sử dụng kiến trúc Microservices và các dịch vụ AWS được lựa chọn cẩn thận nhằm tối đa hóa bảo mật cho dữ liệu nhân sự nhạy cảm.

**Các thành phần Kiến trúc:**

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

- **DevOps & Monitoring (DevOps & Giám sát):**
  - **AWS CodePipeline & CodeBuild:** Tự động hóa quy trình CI/CD (Continuous Integration/Continuous Deployment) từ mã nguồn đến môi trường production.
  - **Amazon CloudWatch & SNS:** Giám sát tình trạng hệ thống và gửi cảnh báo khi có sự cố xảy ra.

#### Mục tiêu Workshop

Sau khi hoàn thành workshop này, bạn sẽ:

1. Xây dựng hạ tầng mạng an toàn với VPC, Subnets và Security Groups
2. Triển khai tầng dữ liệu với RDS PostgreSQL và ElastiCache Redis trong Private Subnets
3. Đóng gói và triển khai ứng dụng Java Spring Boot sử dụng Docker và Elastic Beanstalk
4. Triển khai CI/CD pipeline tự động với CodeBuild và CodePipeline
5. Tối ưu hiệu suất sử dụng CloudFront CDN và S3 cho static assets
6. Tăng cường bảo mật với AWS WAF để bảo vệ khỏi các cuộc tấn công web phổ biến
7. Thiết lập giám sát và cảnh báo với CloudWatch và SNS
8. Học các quy trình dọn dẹp tài nguyên đúng cách để tránh chi phí không mong muốn

#### Nội dung

1. [Giới thiệu Hệ thống HRM](5.1-Workshop-overview/)
2. [Các bước chuẩn bị](5.2-Prerequiste/)
3. [Thiết lập Hạ tầng Mạng](5.3-S3-vpc/)
4. [Triển khai Tầng Dữ liệu](5.4-S3-onprem/)
5. [Triển khai Ứng dụng](5.5-Policy/)
6. [Tự động hóa CI/CD](5.6-Cleanup/)
7. [Tối ưu hóa & Bảo mật](5.7-Section7/)
8. [Giám sát & Vận hành](5.8-Section8/)
9. [Dọn dẹp Tài nguyên](5.9-Section9/)
