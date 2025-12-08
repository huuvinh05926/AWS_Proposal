---
title: "Week 6 Worklog"
date: "2025-11-11"
weight: 1
chapter: false
pre: " <b> 1.6. </b> "
---

### Week 6 Objectives:

- Understand basic concepts of **Database Concepts** and **RDBMS / NoSQL**.
- Distinguish **OLTP**, **OLAP**, and corresponding data systems.
- Master the structure and roles of **Primary Key**, **Foreign Key**, **Index**, **Partition**, **Buffer**, **Log**.
- Learn about database services on AWS such as **Amazon RDS**, **Aurora**, **Redshift**, **ElastiCache**.
- Know how to **optimize, recover, scale, and secure** databases on AWS platform.

### Tasks to be carried out this week:

| Day | Task                                                                                                                | Start Date | Completion Date | Reference Material                        |
| --- | ------------------------------------------------------------------------------------------------------------------- | ---------- | --------------- | ----------------------------------------- |
| 2   | Review database concepts: Database, Session, Primary/Foreign Key, Index, Partition, Buffer, Execution Plan, DB Log. | 09/15/2025 | 09/15/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 3   | Learn about **RDBMS** (relational model, SQL) and **NoSQL** (Document, Key-Value, Graph, Wide-column).              | 09/16/2025 | 09/16/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 4   | Compare **OLTP** and **OLAP**, determine suitable application types and the role of Data Warehouse.                 | 09/17/2025 | 09/17/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 5   | Learn about **Amazon RDS**: architecture, features (backup, read replica, failover, scaling, encryption).           | 09/18/2025 | 09/18/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 6   | Learn about **Amazon Aurora**: read/write performance, backtrack, clone, global DB, multi-master.                   | 09/19/2025 | 09/19/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 7   | Learn about **Amazon Redshift** and **ElastiCache**, applications for OLAP and caching.                             | 09/20/2025 | 09/20/2025      | <https://cloudjourney.awsstudygroup.com/> |

---

### Week 6 Achievements:

#### 🧩 **Database Concept**

- **Database (CSDL)**: structured/semi-structured information system stored on devices to serve concurrent access from multiple applications.
- **Session**: time period from connection to disconnection with database system.
- **Primary Key**: uniquely identifies each record in a table.
- **Foreign Key**: links between tables through reference to primary key.
- **Index**: data structure that helps **speed up access**, but consumes **memory and write cost**.
- **Partition**: divides large tables into multiple parts for **faster queries**.
- **Execution Plan**: query execution plan created by **query optimizer** to choose the most efficient method.
- **DB Log**: records changes to help **recover and synchronize between primary–replica**.
- **Buffer**: temporary memory area to **speed up read/write data** before synchronizing with disk.

---

#### **RDBMS & NoSQL**

- **RDBMS (Relational Database Management System)**:

  - Data organized in tables, rows, columns; relationships between tables represented by **keys**.
  - Uses **SQL** to query and manage data.
  - Ensures data integrity, supports ACID (Atomicity, Consistency, Isolation, Durability).

- **NoSQL (Not only SQL)**:
  - Does not store data in tables, has flexible structure.
  - Popular types:
    - **Document-based**: MongoDB.
    - **Key-Value**: Redis, DynamoDB.
    - **Wide-column**: Cassandra.
    - **Graph**: Neo4j.
  - Suitable for **big data** applications, **unstructured**, **flexible scaling**.

---

#### **OLTP vs OLAP**

| Feature        | OLTP                           | OLAP                                     |
| -------------- | ------------------------------ | ---------------------------------------- |
| Purpose        | Process real-time transactions | Analyze historical data                  |
| Data           | Frequently updated             | Aggregated, read-only                    |
| Applications   | Banking, retail, ticketing     | Reports, BI, analysis                    |
| Focus          | Transaction processing speed   | Query response speed                     |
| AWS Technology | **RDS**, **Aurora**            | **Redshift**, **Athena**, **QuickSight** |

---

#### **Amazon RDS (Relational Database Service)**

- Fully managed database service.
- Supports: **Aurora, MySQL, PostgreSQL, MariaDB, Oracle, MSSQL**.
- **Key features:**
  1. **Automatic backup** (DB + Log, kept up to 35 days).
  2. **Read Replica** supports read workload (reporting).
  3. **Automatic failover** between Primary/Standby (Multi-AZ).
  4. **Encryption at rest & in transit**.
  5. **Auto scaling storage & instance size**.
  6. **Security via Security Group and NACL**.
  7. Commonly used for **OLTP applications**.

---

#### **Amazon Aurora**

- RDBMS optimized for high performance, compatible with **MySQL** and **PostgreSQL**.
- Inherits all RDS features, adds characteristics:
  - **Backtrack** – restores DB to previous point in time.
  - **Clone** – creates fast copy.
  - **Global Database** – multiple regions with 1 master, many read replicas.
  - **Multi-master** – supports parallel writes from multiple nodes.
- Data stored distributed and automatically synchronized across multiple AZs.

---

#### **Amazon Redshift**

- **Data Warehouse** service managed by AWS, core is **PostgreSQL** optimized for OLAP.
- Uses **Massively Parallel Processing (MPP)** architecture:
  - **Leader Node** coordinates queries.
  - **Compute Node** stores and processes data.
- Stores data **in columns (Columnar Storage)** → optimized for analysis.
- Supports:
  - **SQL, JDBC, ODBC**.
  - **Redshift Spectrum** – queries data directly in S3.
  - **Transient cluster** – saves cost when paused.

---

#### **Amazon ElastiCache**

- Fully managed **caching engine** service.
- Supports two engines: **Redis** and **Memcached**.
- Helps **reduce database load**, increases data access performance.
- AWS automatically detects and replaces failed nodes.
- Redis usually recommended more because of:
  - Rich features (replication, persistence, pub/sub).
  - High performance and good scalability.
- Need to **manage caching logic in application** to ensure data consistency.

---

- View EC2 service
- Create and manage key pairs
- Check information about running services
- ...

- Acquired the ability to connect between the web interface and CLI to manage AWS resources in parallel.
- ...
