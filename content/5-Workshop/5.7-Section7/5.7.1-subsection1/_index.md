---
title: "Configure S3 & CloudFront"
date: "2025-11-11"
weight: 1
chapter: false
pre: " <b> 5.7.1 </b> "
---

#### Configure S3 & CloudFront

**1. Create S3 Bucket:**

- Create Bucket (e.g., **minimarket-assets-prod**)
- **Block Public Access**: On

![s31](/images/5-Workshop/5.7-Img/s31.png)

![s32](/images/5-Workshop/5.7-Img/s32.png)

- Manually upload the **images** folder from the code to this Bucket

![s33](/images/5-Workshop/5.7-Img/s33.png)

**2. Create CloudFront Distribution:**

- **Origin type**: Select **Elastic Load Balancer**
- **Origin Domain**: Select the Beanstalk Load Balancer

![LB1](/images/5-Workshop/5.7-Img/LB1.png)
![LB2](/images/5-Workshop/5.7-Img/LB2.png)

- **Settings**: Select **Customize origin settings**
- **Protocol**: HTTP Only

![LB3](/images/5-Workshop/5.7-Img/LB3.png)

- **Cache settings**: Select **Customize cache settings**
- **Viewer Protocol Policy**: Redirect HTTP to HTTPS

![LB4](/images/5-Workshop/5.7-Img/LB4.png)

**3. Add S3 Origin (For images):**

- Go to the newly created Distribution

![LB5](/images/5-Workshop/5.7-Img/LB5.png)

- Go to the **Origins** tab > **Create Origin**

![LB6](/images/5-Workshop/5.7-Img/LB6.png)

- **Origin domain**: Select the S3 bucket created earlier (minimarket-assets-prod)

![LB7](/images/5-Workshop/5.7-Img/LB7.png)

- **Origin Access**: Select **Origin access control (OAC)** > **Create new OAC**

![LB8](/images/5-Workshop/5.7-Img/LB8.png)

![LB9](/images/5-Workshop/5.7-Img/LB9.png)

- **Bucket Policy**: Copy the policy provided by CloudFront and paste it into the S3 Bucket policy

![LB10](/images/5-Workshop/5.7-Img/LB10.png)

![LB11](/images/5-Workshop/5.7-Img/LB11.png)

![LB12](/images/5-Workshop/5.7-Img/LB12.png)

![LB13](/images/5-Workshop/5.7-Img/LB13.png)

**4. Configure Behavior:**

- Return to CloudFront and go to the **Behaviors** tab

![LB14](/images/5-Workshop/5.7-Img/LB14.png)

- Create Behavior with **Path pattern**: `/images/`
- Point to **Origin S3**

![LB15](/images/5-Workshop/5.7-Img/LB15.png)

- **Cache Policy**: CachingOptimized

![LB16](/images/5-Workshop/5.7-Img/LB16.png)
