---
title: "Giám sát & Vận hành"
date: "2025-11-11"
weight: 8
chapter: false
pre: " <b> 5.8. </b> "
---

#### Giám sát & Vận hành

#### Tổng quan

Một hệ thống Production không thể được coi là hoàn thiện nếu thiếu khả năng **Giám sát (Monitoring)** và **Cảnh báo (Alerting)**. Bạn không thể ngồi nhìn màn hình 24/7 để kiểm tra xem Server có còn sống hay không.

Trong module này, chúng ta sẽ thiết lập cho hệ thống giám sát và cảnh báo cho MiniMarket bằng các dịch vụ quản lý vận hành của AWS:

- **Amazon CloudWatch**: Thu thập các chỉ số (Metrics) từ EC2, RDS, ELB
- **Amazon SNS (Simple Notification Service)**: Dịch vụ gửi thông báo. Chúng ta sẽ dùng nó để gửi Email cho người quản trị khi hệ thống gặp sự cố

Chúng ta sẽ thiết lập một **CloudWatch Alarm** để theo dõi CPU của Web Server. Nếu CPU vượt quá 70% (dấu hiệu quá tải hoặc bị tấn công), hệ thống sẽ tự động kích hoạt SNS để gửi Email cảnh báo khẩn cấp.

![Monitoring Architecture](/images/5-Workshop/5.8-Section8/monitoring-diagram.png)

#### Nội dung

- [Thiết lập Cảnh báo CloudWatch & SNS](5.8.1-subsection1/)
