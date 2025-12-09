---
title: "Event 4"
date: "2025-11-29"
weight: 4
chapter: false
pre: " <b> 4.4. </b> "
---

# 29/11/2025

# AWS IAM Security Best Practices

## Thông tin diễn giả

- **Huỳnh Hoàng Long** - AWS Expert
- **Đinh Lê Hoàng Anh** - Cloud Engineer Trainee, First Cloud Journey

## IAM là gì?

IAM (Identity and Access Management) là dịch vụ quản lý danh tính và quyền truy cập của AWS, cho phép quản lý **roles** với quyền hạn nhất định và gán cho **users** cụ thể, tăng tính bảo mật cho hệ thống.

**Thành phần chính:**

- **Users**: Người dùng cá nhân
- **Groups**: Nhóm người dùng
- **Roles**: Vai trò với quyền hạn cụ thể
- **Policies**: Chính sách định nghĩa quyền hạn

## IAM Best Practices

### 1. Principle of Least Privilege

**Không cấp quá nhiều quyền**, chỉ cấp quyền tối thiểu cần thiết.

- Giảm rủi ro khi account bị xâm nhập
- Hạn chế thiệt hại nếu có sự cố
- Developer chỉ cần quyền deploy, không cần quyền xóa database

### 2. Xóa Root Access Keys

**Xóa root access key ngay sau khi setup.**

- Root có quyền hạn cao nhất
- Không dùng root cho công việc hàng ngày
- Lưu root credentials ở nơi an toàn

### 3. Tránh Wildcard (\*)

**Không dùng "\*"** vì nó cấp toàn quyền.

```json
// Tránh
{"Action": "*", "Resource": "*"}

// Nên dùng
{"Action": ["s3:GetObject", "s3:PutObject"],
 "Resource": "arn:aws:s3:::my-bucket/*"}
```

### 4. Sử dụng AWS SSO

**AWS SSO thay vì IAM users thông thường.**

- Credentials tự động reset (15 phút - 36 giờ)
- Tăng bảo mật, quản lý tập trung

## Single Sign-On (SSO)

![Credentials Spectrum](/images/4-EventParticipated/7E18B68B-FAF5-48D7-8216-46DAE1FB7B90.jpeg)

**SSO** cho phép đăng nhập 1 lần truy cập nhiều hệ thống.

**Lợi ích:**

- Quản lý nhiều roles và accounts dễ dàng
- Không cần login lại khi chuyển app
- Kích hoạt SSO đồng thời kích hoạt AWS Organizations

## Multi-Factor Authentication (MFA)

![Multi-Factor Authentication (MFA)](/images/4-EventParticipated/312A5E8A-5CC2-4087-8D9C-B04BC59C5B03.jpeg)

**MFA** là bước xác thực bổ sung, bảo vệ account ngay cả khi mật khẩu bị lộ.

**Các loại:**

- Virtual MFA: Google/Microsoft Authenticator, Authy
- Hardware: YubiKey, Gemalto tokens
- SMS OTP (ít bảo mật)

**Best practices:** Bắt buộc MFA cho tất cả users, ưu tiên Virtual/Hardware MFA.

## Password Policies

**Chính sách mật khẩu mạnh:**

- Độ dài: 12-14 ký tự
- Độ phức tạp: Chữ hoa, thường, số, ký tự đặc biệt
- Expiration: 60-90 ngày
- Không tái sử dụng 5 mật khẩu gần nhất

## Service Control Policies (SCP)

**SCP** định nghĩa quyền hạn tối đa trong account/OU.

- Không cấp quyền, chỉ giới hạn quyền
- Áp dụng ở cấp AWS Organizations
- Override mọi IAM policies

## Permission Boundaries

**Permission Boundaries** đặt giới hạn quyền tối đa cho IAM entity.

**Use cases:**

- Cho phép developers tạo roles nhưng không vượt boundary
- Ngăn privilege escalation

## Credentials Rotation

**AWS Secrets Manager** tự động rotation:

1. Tạo credentials mới
2. Test credentials
3. Áp dụng vào app
4. Xóa credentials cũ

**Best practices:** Rotate access keys ít nhất 90 ngày, sử dụng IAM roles khi có thể.

## IAM Access Analyzer

![IAM Access Analyzer](/images/4-EventParticipated/AADDB3CC-6E5D-4B91-9DE2-28C7A00B915A.jpeg)

**IAM Access Analyzer** phân tích và giám sát quyền truy cập:

- Phát hiện resources shared với external entities
- Validate policy syntax
- Đề xuất least-privilege policies

**Findings thường gặp:**

- S3 buckets public/shared external
- KMS keys accessible từ bên ngoài
- IAM roles có thể assume từ external accounts

## Key Takeaways

### Về IAM Security

1. **Least Privilege**: Chỉ cấp quyền tối thiểu cần thiết
2. **Delete Root Keys**: Xóa root access keys ngay sau setup
3. **Enable MFA**: Bắt buộc MFA cho tất cả users
4. **Use AWS SSO**: Thay vì IAM users thông thường
5. **Rotate Credentials**: Định kỳ 90 ngày hoặc sử dụng IAM roles
6. **Use IAM Access Analyzer**: Phát hiện overly permissive policies
7. **Implement SCP**: Đặt guardrails ở organization level
8. **Password Policies**: Enforce strong password requirements

---

## Kết quả và Giá trị đạt được

### Kiến thức thu được:

- Hiểu sâu về **IAM (Identity and Access Management)** và vai trò quan trọng trong bảo mật AWS
- Nắm vững **8 best practices** quan trọng nhất về IAM security
- Học được về **AWS SSO** và lợi ích của việc sử dụng temporary credentials
- Hiểu cách hoạt động của **MFA (Multi-Factor Authentication)** và các loại MFA
- Nắm rõ về **Service Control Policies (SCP)** và **Permission Boundaries**
- Học được cách sử dụng **IAM Access Analyzer** để phát hiện security risks

### Kỹ năng phát triển:

- Kỹ năng thiết kế IAM policies theo nguyên tắc **Least Privilege**
- Khả năng phân biệt và sử dụng đúng IAM Users, Groups, Roles và Policies
- Biết cách implement **credentials rotation** tự động với AWS Secrets Manager
- Hiểu cách setup và enforce **password policies** mạnh
- Nâng cao kỹ năng audit và analyze IAM permissions

### Bài học quan trọng:

- **Never use root account** cho công việc hàng ngày - chỉ dùng trong emergency
- **Avoid wildcards (\*)** trong IAM policies - luôn specify cụ thể resources và actions
- **MFA is mandatory** - đặc biệt cho privileged accounts
- **Temporary credentials** (SSO, STS) an toàn hơn long-term access keys
- **Regular audits** với IAM Access Analyzer để phát hiện security gaps
- **Defense in depth**: Sử dụng multiple layers (IAM policies, SCP, Permission Boundaries)

### Ứng dụng thực tế:

- Có thể áp dụng ngay các best practices vào AWS accounts hiện tại
- Biết cách setup AWS Organizations và implement SCPs
- Hiểu cách integrate AWS SSO với corporate identity providers
- Có thể design IAM architecture an toàn cho production environments

### Security mindset:

- **Assume breach**: Thiết kế hệ thống giả định rằng credentials có thể bị compromise
- **Least privilege by default**: Start với no permissions, add chỉ khi cần
- **Audit regularly**: Review IAM policies và access patterns thường xuyên
- **Automate security**: Sử dụng tools như Access Analyzer để detect issues sớm

### Giá trị mang lại:

- Nâng cao đáng kể awareness về IAM security
- Có framework cụ thể để implement IAM best practices
- Giảm thiểu risks của security breaches thông qua proper access management
- Chuẩn bị tốt cho AWS Security Specialty certification

2. **No Root Keys**: Không dùng root cho công việc hàng ngày
3. **Avoid Wildcards**: Chỉ định rõ actions và resources
4. **Enable MFA**: Bắt buộc cho tất cả users

### Về Authentication

1. **AWS SSO**: Tập trung quản lý, auto-rotate credentials
2. **MFA**: Lớp bảo mật quan trọng
3. **Strong Passwords**: Phức tạp, rotation định kỳ
4. **Temporary Credentials**: Ưu tiên IAM roles

### Về Governance

1. **SCP**: Giới hạn quyền cấp organization
2. **Permission Boundaries**: Ngăn privilege escalation
3. **Credentials Rotation**: Tự động với Secrets Manager
4. **Access Analyzer**: Giám sát liên tục

## Trải nghiệm tại sự kiện

Tham gia workshop **"AWS IAM Security Best Practices"** giúp tôi hiểu sâu về bảo mật AWS.

### Học hỏi từ experts

- Anh Long và anh Anh chia sẻ kinh nghiệm thực chiến với IAM
- Case studies về security incidents và cách phòng tránh
- Best practices từ doanh nghiệp lớn

### Insights quan trọng

- **Least Privilege**: Yêu cầu bắt buộc, không chỉ lý thuyết
- **Defense in Depth**: Nhiều lớp bảo mật (MFA, SCP, Permission Boundaries)
- **Automation**: Credential rotation tự động giảm rủi ro

### Tools chính

- **AWS SSO**: Enterprise authentication hiện đại
- **IAM Access Analyzer**: Audit và validate policies
- **Secrets Manager**: Quản lý credentials tự động

### Ứng dụng vào công việc

1. **Audit permissions**: Review và tighten policies
2. **Enable MFA**: Triển khai cho tất cả users
3. **Setup SSO**: Migrate từ IAM users
4. **Credential rotation**: Sử dụng Secrets Manager
5. **Access Analyzer**: Monitor security findings

> Tổng kết, workshop nhấn mạnh security mindset - least privilege, nhiều lớp bảo mật, và giám sát liên tục.
