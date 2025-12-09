---
title: "Tạo Build Project"
date: "2025-11-11"
weight: 1
chapter: false
pre: " <b> 5.6.1 </b> "
---

#### Tạo Build Project

1. Truy cập **CodeBuild** > **Create project**

![cicd1](/images/5-Workshop/5.6-Cleanup/cicd1.png)

2. **Project name**: MiniMarket-Build

![cicd2](/images/5-Workshop/5.6-Cleanup/cicd2.png)

3. **Source**: Chọn **GitHub** (Kết nối tới Repo chứa code)

![cicd3](/images/5-Workshop/5.6-Cleanup/cicd3.png)

4. **Environment**:
   - **Environment image**: Managed Image
   - **Operating system**: Amazon Linux
   - **Runtime**: Standard
   - **Image**: 5.0
   - **Service role**: New service role

![cicd4](/images/5-Workshop/5.6-Cleanup/cicd4.png)

![cicd5](/images/5-Workshop/5.6-Cleanup/cicd5.png)

5. **Privileged**: Enable (Bắt buộc để chạy lệnh Docker build)

![cicd6](/images/5-Workshop/5.6-Cleanup/cicd6.png)

6. **Buildspec**: Use a buildspec file

![cicd7](/images/5-Workshop/5.6-Cleanup/cicd7.png)

7. Bấm **Create build project**

{{% notice tip %}}
Sau khi tạo xong, vào **IAM Role** của CodeBuild vừa tạo, cấp thêm quyền **AmazonEC2ContainerRegistryPowerUser** để nó có thể đẩy ảnh lên ECR.
{{% /notice %}}
