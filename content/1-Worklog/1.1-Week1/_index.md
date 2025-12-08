---
title: "Week 1 Worklog"
date: "2025-11-11"
weight: 1
chapter: false
pre: " <b> 1.1. </b> "
---

### Week 1 Objectives:

- Connect and get acquainted with members of **First Cloud Journey (FCJ)**.
- Understand basic AWS services, how to use **AWS Management Console** and **AWS CLI**.

---

### Tasks to be carried out this week:

| Day | Task                                                                                                                                                                                                       | Start Date | Completion Date | Reference Material                        |
| --- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------- | --------------- | ----------------------------------------- |
| 2   | - Get acquainted with FCJ members. <br> - Read and understand the rules and regulations at the internship unit.                                                                                            | 08/11/2025 | 08/11/2025      |                                           |
| 3   | - Set up & manage AWS via **Console** and **CLI**.                                                                                                                                                         | 08/12/2025 | 08/12/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 4   | - Create AWS Free Tier account. <br> - Learn about AWS Console & AWS CLI. <br> - **Practice:** <br>&emsp; + Create AWS account. <br>&emsp; + Install AWS CLI & configure. <br>&emsp; + Use AWS CLI basics. | 08/13/2025 | 08/13/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 5   | - Learn basic EC2: <br>&emsp; + Instance types, AMI, EBS,... <br> - Methods to remote SSH into EC2. <br> - Learn about **Elastic IP**.                                                                     | 08/14/2025 | 08/15/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 6   | - **Practice:** <br>&emsp; + Launch EC2 instance. <br>&emsp; + Connect via SSH. <br>&emsp; + Attach EBS volume.                                                                                            | 08/15/2025 | 08/15/2025      | <https://cloudjourney.awsstudygroup.com/> |

---

### Week 1 Achievements:

- Learned how to **draw AWS architecture** on draw.io and use standard **AWS Architecture Icons**.

- Successfully **created and configured AWS Free Tier account**:

  - Understood the concept of **Root Account** and **IAM User**.
  - Created **IAM Group** and **IAM User**, assigned admin permissions.
  - Distinguished **Access Key/Secret Key** (CLI) and **Console Password** (Web login).

- Became familiar with **AWS Management Console**:

  - Knew how to log in and navigate the web interface.
  - Managed **User Groups**, **Users**, and **Permissions** in IAM.
  - Understood the significance of setting passwords for users.

- Installed and configured **AWS CLI v2** on computer:

  - Set up Access Key, Secret Key, default Region.
  - Connected CLI to AWS account using command:
    ```bash
    aws sts get-caller-identity
    ```

- Used **AWS CLI** to perform basic operations:

  - Checked account information (`aws sts get-caller-identity`).
  - Retrieved list of regions (`aws ec2 describe-regions`).
  - Viewed EC2 information (`aws ec2 describe-instances`).
  - Created and managed key pairs (`aws ec2 create-key-pair`).
  - Uploaded files to S3 (`aws s3 cp <file> s3://<bucket>`).

- Acquired the ability to combine **Console and CLI** to manage AWS resources in parallel.

- Additional learning:
  - How to create **domain** via **Route 53**.
  - Introduction to **CDN**, **AWS WAF**, and other security services.
  - Managing **spending on AWS Billing Dashboard**.
  - Learning about **AWS Support Plans**.

---
