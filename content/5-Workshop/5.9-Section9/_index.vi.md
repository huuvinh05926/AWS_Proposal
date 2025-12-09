---
title: "Dọn dẹp tài nguyên"
date: "2025-11-11"
weight: 9
chapter: false
pre: " <b> 5.9. </b> "
---

#### Dọn dẹp tài nguyên

#### Tổng quan

Chúc mừng bạn đã hoàn thành việc di chuyển và triển khai thành công **Hệ thống Quản lý Nhân sự (HRM)** lên hạ tầng AWS Cloud!

Tuy nhiên, công việc của chúng ta chưa kết thúc. Bước cuối cùng và cũng là bước quan trọng nhất để bảo vệ ngân sách của bạn chính là **Dọn dẹp Tài nguyên** đã triển khai trong Workshop.

Các dịch vụ chúng ta đã sử dụng như **Amazon RDS for PostgreSQL**, **NAT Gateway**, **Elastic Load Balancer (ELB)**, **AWS ElastiCache (Redis)**, và các **EC2 Instance** chạy ứng dụng Java Spring Boot đều tính phí theo giờ, dù bạn có sử dụng ứng dụng hay không. Nếu quên xóa, hóa đơn cuối tháng có thể rất cao.

Chúng ta sẽ thực hiện quy trình **Decommissioning (vô hiệu hóa/dỡ bỏ)** hệ thống theo đúng trình tự để đảm bảo rằng không còn tài nguyên nào bị sót lại gây phát sinh chi phí ngầm.

#### Nội dung

- [Quy trình xóa tài nguyên an toàn](5.9.1-subsection1/)
