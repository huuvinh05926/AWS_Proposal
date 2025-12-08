---
title: "Worklog Tuần 8"
date: "2025-11-11"
weight: 1
chapter: false
pre: " <b> 1.8. </b> "
---

### Mục tiêu tuần 8:

- Tìm hiểu CloudFront (CDN): Chức năng CDN, Cache Policy, Origin Access Control (OAC).
- Hiểu Route 53 & DNS: Domain, Hosted Zone, các loại Record.
- Học về WAF (Web Application Firewall) và bảo mật ứng dụng web.

### Các công việc cần triển khai trong tuần này:

| Thứ | Nội dung Học/Research                                                   | Công việc Thực hành & Code                                                                                                  | AWS Event đã xem                              |
| --- | ----------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------- |
| 2   | CloudFront (CDN): Tìm hiểu chức năng CDN, cơ chế phân phối nội dung.    | Khởi tạo CloudFront Distribution cơ bản, tìm hiểu cấu trúc.                                                                 | Optimizing Performance with Amazon CloudFront |
| 3   | CloudFront Advanced: Cache Policy, Origin Access Control (OAC).         | Thiết lập CDN: Kết nối CloudFront với S3 bucket (Frontend) làm Origin.                                                      |                                               |
| 4   | CloudFront Configuration: TTL, CORS, Behavior settings.                 | Cấu hình TTL và CORS cho CloudFront Distribution, kiểm tra cache hoạt động.                                                 |                                               |
| 5   | Route 53 & DNS: Domain, Hosted Zone, các loại Record (A, AAAA, CNAME).  | Liên kết Domain: Cấu hình Route 53 Hosted Zone.                                                                             | AWS Networking Fundamentals                   |
| 6   | Route 53 Practice: Tạo và quản lý DNS records.                          | Tạo record A để trỏ domain chính thức tới CloudFront Distribution.                                                          |                                               |
| 7   | WAF (Web Application Firewall): Chức năng, các mối đe dọa OWASP Top 10. | Tăng cường Bảo mật: Tạo WebACL trong AWS WAF, gắn WAF vào CloudFront. Viết thử Rule cơ bản để chặn các mối đe dọa phổ biến. |                                               |

### Kết quả đạt được tuần 8:

- Hiểu rõ về **Amazon CloudFront (CDN)**:

  - Cơ chế phân phối nội dung qua Edge Locations
  - Cache Policy và cách tối ưu hiệu năng
  - Origin Access Control (OAC) để bảo mật

- Thành công trong việc thiết lập CDN:

  - Tạo CloudFront Distribution
  - Kết nối S3 bucket làm Origin cho Frontend
  - Cấu hình TTL và CORS phù hợp

- Nắm được **Route 53 & DNS**:

  - Hiểu khái niệm Domain và Hosted Zone
  - Phân biệt các loại Record (A, AAAA, CNAME)
  - Cách quản lý DNS trên AWS

- Liên kết domain thành công:

  - Cấu hình Route 53 Hosted Zone
  - Tạo record A trỏ domain tới CloudFront Distribution
  - Kiểm tra truy cập qua domain chính thức

- Hiểu về **AWS WAF** và bảo mật web:

  - Chức năng của Web Application Firewall
  - Các mối đe dọa OWASP Top 10
  - Cách viết Rule để bảo vệ ứng dụng

- Tăng cường bảo mật thành công:

  - Tạo WebACL trong AWS WAF
  - Gắn WAF vào CloudFront Distribution
  - Viết và test Rule cơ bản để chặn các mối đe dọa phổ biến

- Tham gia các AWS Events:
  - Optimizing Performance with Amazon CloudFront
  - AWS Networking Fundamentals
