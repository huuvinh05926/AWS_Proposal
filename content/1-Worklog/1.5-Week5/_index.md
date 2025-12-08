---
title: "Week 5 Worklog"
date: "2025-11-11"
weight: 1
chapter: false
pre: " <b> 1.5. </b> "
---

### Week 5 Objectives:

- Understand clearly the **Shared Responsibility Model** and security responsibilities between AWS and customers.
- Master the **Identity and Access Management (IAM)** mechanism — users, groups, roles, policies.
- Learn about **AWS Organization**, **AWS Identity Center**, and **AWS KMS** in security management.
- Know how to **assign permissions, encrypt, and audit security** in AWS environment.
- Get familiar with **Amazon Cognito** and **AWS Security Hub**.

### Tasks to be carried out this week:

| Day | Task                                                                                                                                                                                     | Start Date | Completion Date | Reference Material                        |
| --- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------- | --------------- | ----------------------------------------- |
| 2   | Learn about **Shared Responsibility Model**: division of responsibilities between AWS and customers; service classification by management level (Infrastructure, Hybrid, Fully-managed). | 09/08/2025 | 09/08/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 3   | Study **Root Account** and **best practices**: create IAM admin user, lock root credentials, protect domain/email information.                                                           | 09/09/2025 | 09/09/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 4   | Learn about **IAM Users, Groups, Roles, Policies** — permission mechanism, trust policy, explicit deny.                                                                                  | 09/10/2025 | 09/10/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 5   | Practice creating **IAM Role**, **assume role**, and use **AWS STS (Security Token Service)** to grant temporary permissions.                                                            | 09/11/2025 | 09/11/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 6   | Learn about **Amazon Cognito** (User Pool & Identity Pool) — login mechanism, authentication, and access to AWS resources.                                                               | 09/12/2025 | 09/12/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 7   | Study **AWS Organization**, **Identity Center**, **KMS**, and **Security Hub** — centralized management, data encryption, automatic security assessment.                                 | 09/13/2025 | 09/13/2025      | <https://cloudjourney.awsstudygroup.com/> |

---

### Week 5 Achievements:

- **Shared Responsibility Model**
  - AWS is responsible for **security of the cloud** — hardware, infrastructure, hypervisor.
  - Customers are responsible for **security in the cloud** — service configuration, data, encryption, user management.
  - Level of responsibility changes depending on service type:
    - **Infrastructure (EC2, VPC, EBS)** → customer bears most.
    - **Managed Services (RDS, EKS)** → shared.
    - **Fully Managed (S3, Lambda)** → AWS bears more.

---

- **AWS Root Account**
  - Has full access to all AWS services and resources.
  - Should **lock credentials**, only use in emergencies.
  - **Best practices:**
    - Create **IAM Administrator user** to replace root.
    - **Divide root access** among 2 different managers.
    - Ensure **domain and root account email renewal** regularly.

---

- **AWS Identity and Access Management (IAM)**
  - Is a service to control access to AWS resources.
  - **Principals** include:
    - AWS Root user, IAM user, Federated user (via SAML/OAuth), IAM role, AWS service, Anonymous user.
  - **IAM User**:
    - Has no default permissions.
    - Can log in via **Management Console** or use **Access Key/Secret Key**.
    - Not used to manage applications/operating systems.
  - **IAM Group**:
    - Groups users for easier management (cannot nest groups).
  - **IAM Policy (JSON)**:
    - **Identity-based policy** (attached to Principal).
    - **Resource-based policy** (attached to Resource).
    - Always prioritizes **explicit Deny > Allow**.
  - **IAM Role**:
    - Has no fixed credentials, only used when **assumed**.
    - **Trust policy** determines who can assume role.
    - Used for cross-account access or granting permissions to **AWS services (like EC2)**.
    - Associated with **AWS STS** to grant temporary credentials.

---

- **Amazon Cognito**
  - Service for **user authentication and management** for web/mobile apps.
  - Consists of 2 components:
    - **User Pool** – stores, registers, and authenticates users.
    - **Identity Pool** – grants access to AWS services.
  - Supports login via **username/password** or **third-party (Facebook, Google, Amazon)**.
  - User Pool combines with Identity Pool to directly access AWS resources after authentication.

---

- **AWS Organization**
  - Allows managing **multiple AWS accounts** within the same organization.
  - Supports **OU (Organizational Units)** and **Consolidated Billing**.
  - Can assign **Service Control Policy (SCP)** to set maximum permission limits on OU/account.
  - SCP is **deny-based**, does not grant permissions but only sets boundaries.

---

- **AWS Identity Center (formerly SSO)**
  - Manages access for multiple AWS accounts and external applications.
  - **Identity source** can be:
    - AWS Managed AD
    - On-premises AD (via Trust/Connector)
  - **Permission Set**: set of permissions assigned to user/group → grants role to accounts in Organization.

---

- **AWS Key Management Service (KMS)**
  - Service to create and manage **encryption keys** for data encryption.
  - Supports **Encryption at Rest** meeting **FIPS 140-2** standards.
  - **CMK (Customer Managed Key)** commonly used to create **Data Keys** for actual data encryption.
  - AWS never exports CMK outside the system.

---

- **AWS Security Hub**
  - Service for automatic security auditing based on **AWS Best Practices** and **industry standards**.
  - Runs continuously, evaluates service configurations, and displays **security score**.
  - Supports aggregating security alerts from multiple other services (GuardDuty, Config, Inspector...).

---

- View EC2 service
- Create and manage key pairs
- Check information about running services
- ...

- Acquired the ability to connect between the web interface and CLI to manage AWS resources in parallel.
- ...
