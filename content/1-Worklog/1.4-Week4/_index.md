---
title: "Week 4 Worklog"
date: "2025-11-11"
weight: 1
chapter: false
pre: " <b> 1.4. </b> "
---

### Week 4 Objectives:

- Learn in-depth about **Amazon Simple Storage Service (S3)** and related storage services.
- Understand **object-based storage** structure, distinguish from block storage.
- Master **storage classes**, **lifecycle** policies, **CORS**, and **versioning** mechanisms.
- Learn about **Amazon Glacier**, **Snow Family**, **AWS Storage Gateway**, and **AWS Backup**.
- Understand **RTO/RPO** concepts and Disaster Recovery strategies.

---

### Tasks to be carried out this week:

| Day | Task                                                                                                                                                                                                              | Start Date | Completion Date | Reference Material                        |
| --- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------- | --------------- | ----------------------------------------- |
| 2   | - Introduction to **Amazon S3**: concept, characteristics of object-based storage.<br>- Learn about data replication mechanism, 99.999999% durability and 99.99% availability.                                    | 09/01/2025 | 09/01/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 3   | - Study **bucket, object, key, access point**.<br>- Learn about **storage classes**: Standard, IA, Intelligent Tiering, One Zone, Glacier, Deep Archive.                                                          | 09/02/2025 | 09/02/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 4   | - Configure **S3 lifecycle policy** to automatically transition storage tiers.<br>- Learn about **multipart upload** and **event triggers** when uploading/deleting files.                                        | 09/03/2025 | 09/03/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 5   | - Learn about **S3 hosting static websites**, **CORS policy**, **Access Control List (ACL)**, **Bucket Policy**, **IAM Policy**.<br>- Practice setting up access permissions.                                     | 09/04/2025 | 09/04/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 6   | - Learn about **S3 Versioning**, **S3 Endpoint**, **partition & prefix performance optimization**.<br>- Study **Amazon Glacier**: data retrieval mechanism (Expedited, Standard, Bulk).                           | 09/05/2025 | 09/05/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 7   | - Study **Snow Family (Snowball, Snowball Edge, Snowmobile)**.<br>- Learn about **AWS Storage Gateway** (File, Volume, Tape).<br>- Learn about **AWS Backup**, **RTO/RPO**, and **Disaster Recovery Strategies**. | 09/06/2025 | 09/06/2025      | <https://cloudjourney.awsstudygroup.com/> |

---

### Week 4 Achievements:

- **Mastered knowledge about Amazon S3:**

  - Is an **object storage service**, cannot edit parts but must upload entirely.
  - Data replicated across **3 Availability Zones** in the same region.
  - Supports **trigger events**, **multipart upload**, **versioning**, and **CORS configuration**.

- **Clearly understood storage classes (Storage Class):**

  - **S3 Standard**: frequently accessed data.
  - **S3 Standard-IA** / **One Zone-IA**: infrequently accessed data, lower cost.
  - **S3 Intelligent-Tiering**: automatically moves data between tiers.
  - **S3 Glacier** / **Deep Archive**: long-term storage, slow retrieval, cheap price.

- **Practiced configuring Lifecycle Policy:**

  - Set up automatic object movement after X days between storage classes.
  - Automatically delete old objects after specified time.

- **Learned about CORS and permission mechanisms:**

  - **CORS (Cross-Origin Resource Sharing)** allows web apps to access resources from different domains.
  - **S3 ACL**: basic access permissions by bucket/object.
  - **Bucket Policy / IAM Policy**: define detailed access permissions using JSON policy.

- **Understood clearly about Versioning:**

  - When versioning is enabled, deleting or overwriting does not lose old data.
  - Supports recovering files that were deleted or overwritten incorrectly.

- **Optimized S3 performance:**

  - Use **random prefix** to increase search performance in partitions.
  - Understood **partition & key map hash** mechanism of S3.

- **Amazon Glacier:**

  - Serves long-term data storage with 3 retrieval levels:
    - Expedited (1–5 minutes)
    - Standard (3–5 hours)
    - Bulk (5–12 hours)

- **Snow Family:**

  - **Snowball / Snowball Edge / Snowmobile** used to **migrate large-scale data (TB → EB)** from on-premise to AWS.
  - Can process, encrypt, and compress data before importing to S3 or Glacier.

- **AWS Storage Gateway:**

  - Combines **on-premise + cloud** storage, includes 3 types:
    - **File Gateway (NFS/SMB)** → writes to S3.
    - **Volume Gateway (iSCSI)** → stores block data, snapshots to EBS.
    - **Tape Gateway (VTL)** → stores virtual tapes on S3/Glacier.

- **AWS Backup & Disaster Recovery:**
  - Understood concepts of **RTO (Recovery Time Objective)** and **RPO (Recovery Point Objective)**.
  - Distinguished 4 DR strategies:
    1. Backup & Restore
    2. Pilot Light
    3. Low Capacity Active-Active
    4. Full Capacity Active-Active
  - AWS Backup supports EBS, EC2, RDS, DynamoDB, EFS, Storage Gateway.

---
