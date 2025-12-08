---
title: "Week 3 Worklog"
date: "2025-11-11"
weight: 1
chapter: false
pre: " <b> 1.3. </b> "
---

### Week 3 Objectives:

- Learn in-depth about **Amazon EC2** and related storage services (EBS, EFS, FSx).
- Understand the operating mechanisms, configuration, and pricing options of EC2.
- Practice creating and managing EC2 Instances, EBS Volumes, Snapshots.
- Understand and apply Auto Scaling, Pricing Options, and Lightsail.

---

### Tasks to be carried out this week:

| Day | Task                                                                                                                                                                                             | Start Date | Completion Date | Reference Material                        |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ---------- | --------------- | ----------------------------------------- |
| 2   | - Overview of **Amazon EC2**: concept, scalability, comparison with physical servers.<br>- Learn about **Instance Types**, technical specifications (CPU, Memory, Network, Storage).             | 08/25/2025 | 08/25/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 3   | - Study **AMI (Amazon Machine Image)**, EC2 Instance provisioning process.<br>- Learn about **Hypervisor (KVM, HVM, PV)** and selection mechanisms.                                              | 08/26/2025 | 08/26/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 4   | - Learn about **Key Pair** and login information encryption mechanism (Linux/Windows).<br>- Learn about **EBS (Elastic Block Store)**: HDD types, SSD, snapshot, data replication.               | 08/27/2025 | 08/27/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 5   | - Study **Instance Store**: characteristics, pros/cons, practical applications.<br>- Practice backing up EBS using snapshots and recovery.                                                       | 08/28/2025 | 08/28/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 6   | - Learn about **User Data** and **Metadata** in EC2, how to automate during Instance initialization.<br>- Learn about **EC2 Auto Scaling**, Scaling Policy, Load Balancer integration.           | 08/29/2025 | 08/29/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 7   | - Learn about **Pricing Options**: On-demand, Reserved Instance, Saving Plan, Spot Instance.<br>- Study **Amazon Lightsail**, **EFS**, **FSx**, and **AWS Application Migration Service (MGN)**. | 08/30/2025 | 08/30/2025      | <https://cloudjourney.awsstudygroup.com/> |

---

### Week 3 Achievements:

- Understood clearly the **architecture and operation of Amazon EC2**:

  - Similar to traditional virtual machines but with flexible scalability.
  - Can launch quickly, supports many types of workloads like web, applications, databases...

- Mastered the mechanisms of **EC2 Instance Type**, **AMI**, **Hypervisor**, **Key Pair**.
- Knew how to **create, connect, and backup EC2 Instances** through EBS snapshots.
- Clearly understood the differences between **EBS**, **Instance Store**, **EFS**, and **FSx**:

  - EBS: block storage attached directly to EC2, operates independently via private network.
  - Instance Store: extremely high speed, does not retain data when stopping instance.
  - EFS: shared storage for multiple EC2 (Linux).
  - FSx: similar to EFS but supports NTFS and SMB (Windows/Linux).

- Mastered **EC2 Auto Scaling**:

  - Automatically increases/decreases number of Instances.
  - Supports multiple AZs and integrates with Load Balancer.
  - Can combine multiple Pricing Options.

- Clearly understood the 4 main **Pricing Options**:

  - On-demand: flexible, high price.
  - Reserved Instance & Saving Plan: save when committing long-term.
  - Spot Instance: cheap price, but can be stopped suddenly.

- Knew how to use **Amazon Lightsail** for light workloads, test/dev.
- Understood the mechanism of **AWS Application Migration Service (MGN)** to copy physical/virtual servers to EC2.
- Clearly understood the process of data replication, incremental snapshots, and cost optimization through deduplication.
- Completed **comprehensive documentation and detailed notes** about the entire chain of services related to EC2.

---

- View EC2 service
- Create and manage key pairs
- Check information about running services
- ...

- Acquired the ability to connect between the web interface and CLI to manage AWS resources in parallel.
- ...
