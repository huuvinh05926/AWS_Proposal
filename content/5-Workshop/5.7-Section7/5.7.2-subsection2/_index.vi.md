---
title: "Thiết lập Tường lửa (WAF)"
date: "2025-11-11"
weight: 2
chapter: false
pre: " <b> 5.7.2 </b> "
---

#### Thiết lập Tường lửa (WAF)

1. Truy cập **WAF & Shield** > **Protection packs (webs ACLs)** > **Create protection pack (web ACL)**

![WAF1](/images/5-Workshop/5.7-Img/WAF1.png)

2. **App category**: E-commerce & transaction platforms
   **App focus**: Both API and web

![WAF2](/images/5-Workshop/5.7-Img/WAF2.png)

3. **Add resources** > **Add CloudFront or Amplify resources** > Chọn CloudFront distribution đã tạo ở phần trước

![WAF3](/images/5-Workshop/5.7-Img/WAF3.png)

![WAF4](/images/5-Workshop/5.7-Img/WAF4.png)

4. **Choose initial protections** > **Build your own pack from all of the protections AWS WAF offers** > **AWS-managed rule group**:

![WAF5](/images/5-Workshop/5.7-Img/WAF5.png)

![WAF6](/images/5-Workshop/5.7-Img/WAF6.png)

5. Thêm **Core rule set** (Chặn bot, IP xấu)
6. Thêm **SQL database** (Chặn SQL Injection)

![WAF7](/images/5-Workshop/5.7-Img/WAF7.png)

**Kiểm thử**: Truy cập URL: `https://[domain]/?id=1 OR 1=1`. Nếu nhận lỗi **403 Forbidden**, WAF đã hoạt động.
