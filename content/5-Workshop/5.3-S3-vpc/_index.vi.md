---
title: "Thiết lập Hạ tầng Mạng"
date: "2025-11-11"
weight: 3
chapter: false
pre: " <b> 5.3. </b> "
---

#### 💡 Tổng quan

Trong giai đoạn đầu tiên này, chúng ta sẽ xây dựng nền móng mạng lưới (VPC) vững chắc và bảo mật cho Hệ thống Quản lý Nhân sự (HRM). Việc đảm bảo hạ tầng mạng an toàn là yếu tố tiên quyết để bảo vệ dữ liệu nhân sự nhạy cảm và tuân thủ các quy tắc bảo mật.

Kiến trúc mạng HRM sẽ được thiết kế bao gồm:

- **VPC (Virtual Private Cloud)**: Vùng mạng biệt lập trên AWS.
- **Public Subnet**: Dành cho các thành phần cần giao tiếp trực tiếp với Internet (ví dụ: Internet-facing Load Balancer, NAT Gateway, CloudFront/WAF Endpoints).
- **Private Subnet**: Dành riêng cho các tài nguyên cốt lõi, yêu cầu bảo mật cao, không được truy cập trực tiếp từ Internet (ví dụ: EC2/Webapp Service, Amazon RDS for PostgreSQL, AWS ElastiCache, DynamoDB).
- **NAT Gateway**: Cho phép các máy chủ ứng dụng (App Servers) trong Private Subnet có thể truy cập Internet (ví dụ: để tải các bản cập nhật bảo mật, kéo Docker Image, hoặc kết nối đến các dịch vụ AWS bên ngoài VPC) mà vẫn giữ địa chỉ IP nội bộ không bị lộ ra ngoài.
- **VPC Endpoint (PrivateLink)**: Thiết lập kết nối riêng tư và an toàn giữa VPC của bạn và các dịch vụ AWS khác (như Amazon S3, DynamoDB) mà không cần đi qua Internet, tăng cường bảo mật cho việc tải ảnh Check-in khuôn mặt.

![Network Architecture](/images/5-Workshop/5.3-S3-vpc/infrastructure.png)

#### 📝 Nội dung Thực hiện

- [Khởi tạo VPC & Subnet](5.3.1-create-gwe/)
- [Cấu hình Internet & NAT Gateway](5.3.2-test-gwe/)
- [Cấu hình Route Table](5.3.3-route-table/)
