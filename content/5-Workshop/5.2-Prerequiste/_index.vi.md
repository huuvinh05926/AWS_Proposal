---
title: "Các bước chuẩn bị"
date: "2025-11-11"
weight: 2
chapter: false
pre: " <b> 5.2. </b> "
---

#### Quyền IAM

Gắn quyền AdministratorAccess trong IAM permission policy vào tài khoản AWS để dễ dàng làm việc hơn

**Lưu ý:** Việc sử dụng quyền Administrator chỉ được khuyến nghị cho môi trường Workshop để đảm bảo quá trình triển khai không bị gián đoạn. Trong môi trường Production thực tế, cần tuân thủ nguyên tắc Least Privilege cho từng dịch vụ.

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": "*",
      "Resource": "*"
    }
  ]
}
```

#### Source Code

Repository GitHub chứa code .NET Core và Dockerfile hợp lệ

![Source Code](/images/5-Workshop/5.2-Prerequisite/source-code.png)
