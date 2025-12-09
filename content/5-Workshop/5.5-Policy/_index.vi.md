---
title: "Triển khai Ứng dụng"
date: "2025-11-11"
weight: 5
chapter: false
pre: " <b> 5.5 </b> "
---

#### Tổng quan

Sau khi đã có hạ tầng mạng và dữ liệu, bước tiếp theo là đưa mã nguồn ứng dụng .NET Core lên Cloud. Thay vì quản lý từng máy chủ ảo EC2 thủ công, chúng ta sẽ sử dụng nền tảng Platform-as-a-Service (PaaS) là **AWS Elastic Beanstalk**.

**Mục tiêu của module này:**

- **Containerization**: Đóng gói ứng dụng MiniMarket vào Docker Container để đảm bảo môi trường chạy đồng nhất (Dev = Prod)
- **Deployment**: Triển khai Container lên Elastic Beanstalk. Hệ thống sẽ tự động cấp phát EC2, cấu hình Load Balancer và Auto Scaling Group
- **Connectivity**: Cấu hình để ứng dụng kết nối an toàn tới RDS và Redis thông qua Biến môi trường (Environment Variables)

![App Deployment Architecture](/images/5-Workshop/5.5-Policy/beanstalk-diagram.png)

#### Nội dung

- [Đóng gói ứng dụng với Docker](5.5.1-section1/)
- [Khởi tạo Elastic Beanstalk Environment](5.5.2-section2/)
- [Cấu hình kết nối Database & Redis](5.5.3-section3/)
