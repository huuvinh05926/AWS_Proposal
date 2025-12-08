---
title: "Week 2 Worklog"
date: "2025-11-11"
weight: 1
chapter: false
pre: " <b> 1.2. </b> "
---

### Week 2 Objectives:

- Understand thoroughly the **Amazon VPC** architecture and how network components work in AWS.
- Master the models of **Subnet**, **Route Table**, **Security Group**, **NACL**, **VPC Endpoint**, **Peering**, and **Load Balancer**.
- Know how to choose appropriate connectivity solutions between **on-premises** environments and **AWS Cloud**.

### Tasks to be carried out this week:

| Day | Task                                                                                                                                       | Start Date | Completion Date | Reference Material                        |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------ | ---------- | --------------- | ----------------------------------------- |
| 2   | - Learn about **Amazon VPC** concept & structure, account limits, IPv4/IPv6 CIDR. <br> - Configure basic VPC via Console.                  | 08/18/2025 | 08/18/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 3   | - Learn about **Subnet**, **Availability Zone**, IP addresses. <br> - Create public/private subnets and assign corresponding route tables. | 08/19/2025 | 08/19/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 4   | - Learn about **Route Table**, **Internet Gateway**, **NAT Gateway**, **VPC Endpoint**. <br> - Distinguish interface & gateway endpoints.  | 08/20/2025 | 08/20/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 5   | - **Event:** Attended **Vietnam Cloud Day 2025 – Track 1: GenAI and Data**. <br> - Overview of AI applications in cloud infrastructure.    | 08/21/2025 | 08/21/2025      |                                           |
| 6   | - Study **Security Group**, **Network ACL**, **VPC Flow Logs**. <br> - Practice logging & controlling access between subnets.              | 08/22/2025 | 08/22/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 7   | - Learn about **VPC Peering**, **Transit Gateway**, **VPN**, **Direct Connect**, **Elastic Load Balancer** (ALB, NLB, CLB, GLB).           | 08/23/2025 | 08/23/2025      | <https://cloudjourney.awsstudygroup.com/> |

---

### Week 2 Achievements:

- Understood clearly that **VPC (Virtual Private Cloud)** is a virtual network environment in AWS that helps separate and manage resources by environment (Production/Dev/Test/Staging).

  - Default limit: 5 VPCs per AWS account.
  - Each VPC requires an IPv4 CIDR block (mandatory) and can add IPv6 (optional).

- **Subnet**:

  - Each subnet resides in a specific **Availability Zone**.
  - When creating a subnet, must specify a CIDR within the VPC's CIDR range.
  - AWS reserves the first 5 IP addresses in each subnet for internal use.

- **Route Table**:

  - Defines network routing.
  - Has a default _default route table_ (cannot be deleted) that allows internal communication within the VPC.

- **Elastic Network Interface (ENI)** & **Elastic IP**:

  - ENI is a virtual network card that can be assigned to EC2 and moved between instances.
  - Elastic IP is a static public IPv4 address that can be attached to ENI.

- **VPC Endpoint**:

  - Connects resources in VPC to AWS services without needing Internet.
  - Two types:
    - Interface Endpoint – uses ENI + private IP.
    - Gateway Endpoint – uses route table (supports S3 and DynamoDB).

- **Internet Gateway** & **NAT Gateway**:

  - Internet Gateway: allows EC2 in public subnet to access Internet, managed by AWS, no need for autoscale configuration.
  - NAT Gateway: allows private subnet to access Internet (outbound only).

- **Security Group (SG)** and **Network ACL (NACL)**:

  - SG is a _stateful_ firewall applied to ENI, only has "allow" rules.
  - NACL is a _stateless_ firewall applied to subnet, has "allow/deny" rules and reads from top to bottom.
  - Default: SG blocks inbound, allows outbound; NACL allows all.

- **VPC Flow Logs**:

  - Records IP traffic to/from VPC, subnet, or ENI.
  - Stores on **CloudWatch Logs** or **S3**, does not record packet contents.

- **VPC Peering** & **Transit Gateway**:

  - VPC Peering: direct connection between 2 VPCs (1:1), does not support transitive routing, CIDRs must not overlap.
  - Transit Gateway: hub center connecting multiple VPCs or on-premises networks.

- **VPN Site-to-Site** & **Client-to-Site**:

  - Site-to-Site: connects data center to AWS via **Virtual Private Gateway** and **Customer Gateway**.
  - Client-to-Site: allows 1 host to access resources in VPC (VPN client).

- **AWS Direct Connect**:

  - Creates physical connection from data center to AWS (via Direct Connect Partner in Vietnam).
  - Low latency (~20–30ms), adjustable bandwidth.

- **Elastic Load Balancing (ELB)**:

  - Distributes traffic to multiple EC2/Containers.
  - Has 4 types:
    - **Application Load Balancer (ALB)** – Layer 7, supports path-based routing.
    - **Network Load Balancer (NLB)** – Layer 4, high performance, supports static IP.
    - **Classic Load Balancer (CLB)** – Layer 4 & 7, old, rarely used.
    - **Gateway Load Balancer (GLB)** – Layer 3, uses GENEVE protocol (port 6081).
  - Supports **Sticky Session** and **Access Logs** (stored in S3).

- **Attended Vietnam Cloud Day 2025 - Track 1: GenAI and Data** event which helped understand better how **AWS combines artificial intelligence and big data** to optimize infrastructure, accelerate data analysis, and enhance customer experience in cloud-native systems.
  - View EC2 service
  - Create and manage key pairs
  - Check information about running services
  - ...

* Acquired the ability to connect between the web interface and CLI to manage AWS resources in parallel.
* ...
