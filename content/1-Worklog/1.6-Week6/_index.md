---
title: "Week 6 Worklog"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 1.6. </b> "
---

**Full Name:** Dinh Tuan Minh &emsp; | &emsp; **Student ID:** 2280601918

**Company Mentor:** Nguyen Gia Hung – Head of Solution Architect &emsp; | &emsp; **Academic Supervisor:** Vo Pham Thanh Luan

**Topic:** AWS Database Services

### Week 6 Objectives:

* Systematize foundational database concepts: Relational (SQL) vs Non-Relational (NoSQL), ACID vs BASE, OLTP vs OLAP.
* Master Amazon RDS: architecture, Multi-AZ Deployment, Read Replica, backup/Point-in-Time Recovery, and security.
* Gain deep understanding of Amazon Aurora: distributed 6-way replication storage architecture, Aurora Cluster, Aurora Serverless v2, and Aurora Global Database.
* Learn Amazon Redshift for data warehousing/OLAP and Amazon ElastiCache for caching; practice deploying a 3-tier architecture with RDS and migrating a database with AWS DMS.

### Tasks to be carried out this week:
| Day | Task                                                                                                                                                                                                                    | Start Date | Completion Date | Reference Material                        |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ---------- | --------------- | ----------------------------------------- |
| 2   | - Review database concepts: Relational (SQL) vs Non-Relational (NoSQL), ACID vs BASE, OLTP vs OLAP, deployment models (self-managed, managed, serverless) <br> - Amazon RDS: DB Instance, DB Subnet Group, Parameter/Option Group, Multi-AZ Deployment, Read Replica, backup/PITR, encryption, and network isolation | 05/25/2026 | 05/25/2026      | <https://cloudjourney.awsstudygroup.com/> |
| 3   | - Amazon Aurora: distributed storage architecture (6 copies across 3 AZs), Aurora Cluster (Primary/Replica/Endpoint), Aurora Serverless v2, Aurora Global Database for multi-region | 05/26/2026 | 05/26/2026      | <https://cloudjourney.awsstudygroup.com/> |
| 4   | - Amazon Redshift: Leader/Compute Node architecture, Columnar Storage, Redshift Spectrum, Redshift Serverless <br> - Amazon ElastiCache: Redis (Multi-AZ, Cluster Mode, persistence) and Memcached; caching patterns (Lazy Loading, Write-Through, TTL) | 05/27/2026 | 05/27/2026      | <https://cloudjourney.awsstudygroup.com/> |
| 5   | - **Practice (Lab: Deploying Amazon RDS and Connecting an Application):** <br>&emsp; + Create a 3-tier VPC (public subnet for EC2, private subnet for RDS) <br>&emsp; + Create separate Security Groups for EC2 and RDS, and a DB Subnet Group <br>&emsp; + Create an RDS MySQL instance, deploy an application connecting to the database <br>&emsp; + Practice manual backup and restore from a snapshot | 05/28/2026 | 05/28/2026      | <https://cloudjourney.awsstudygroup.com/> |
| 6   | - **Practice (Lab: AWS Database Migration Service – Database Migration):** <br>&emsp; + Configure SQL Server/Oracle as the source database, use AWS SCT to convert the schema <br>&emsp; + Create a Replication Instance, Endpoints, and a Migration Task (Full Load + CDC) into Aurora MySQL/MySQL <br>&emsp; + Create a DMS Serverless Replication and an SNS Event Notification <br>&emsp; + Troubleshoot memory pressure and table errors during migration <br> - Consolidate knowledge, write the Week 6 report | 05/29/2026 | 05/29/2026      | <https://cloudjourney.awsstudygroup.com/> |
| 7   | - Attended the **First Cloud AI Journey – Workshop & Community Day** event at the AWS Office, Bitexco Tower, Ho Chi Minh City: 6 presentations (AWS Cloud Quest, Hackathon introduction, Why We Always Need Confidence, Tử vi Đại Việt, DevOps Before Disaster, The Iceberg of Procrastination) <br> - Networked with the FCAJ trainee community | 05/30/2026 | 05/30/2026      | First Cloud AI Journey – Workshop & Community Day event |

### Week 6 Achievements:

* Systematized foundational database concepts: SQL vs NoSQL, OLTP vs OLAP, ACID vs BASE, establishing a basis for choosing the right database service for each use case.
* Mastered Amazon RDS: architecture, Multi-AZ HA, Read Replica scale-out, backup/PITR, encryption, and security best practices (private subnet, Security Group isolation).
* Gained deep understanding of Amazon Aurora: its distinctive 6-way replication storage architecture, Aurora Cluster endpoints, Aurora Serverless v2, and Aurora Global Database for multi-region.
* Learned when to use RDS versus Aurora: Aurora suits large workloads requiring high performance and maximum availability; RDS suits cases needing a specific engine or smaller workloads.
* Learned Amazon Redshift as an MPP data warehouse solution for OLAP, clearly distinguishing Redshift's role (analytics) from RDS/Aurora (transactional).
* Understood Amazon ElastiCache Redis and Memcached: caching patterns, and the use-case distinction between Redis (rich data structures, persistence) and Memcached (simple caching, multi-threaded).
* Practiced deploying a 3-tier architecture with RDS in a private subnet — the foundational architecture of every production web application on AWS.
* Practiced the full database migration process with DMS + SCT: heterogeneous migration, CDC replication, DMS Serverless, event notifications, and real-world error troubleshooting.
* Attended the First Cloud AI Journey – Workshop & Community Day community event, gaining additional soft skills (confidence, overcoming procrastination), DevOps insight, and a real-world case study on weighing costs before moving a product to AWS.

### Challenges and Solutions:

| Challenge | Solution |
| --- | --- |
| Difficult to determine when to use RDS versus Aurora for a specific project. | Compared by performance, engine compatibility (Oracle/MSSQL), and cost to make an appropriate choice. |
| Configuring CDC (Change Data Capture) in a heterogeneous migration (Oracle → MySQL) has many steps that are easy to get wrong. | Followed AWS SCT's sequential checklist: configure Supplemental Logging, create a DMS user with the correct permissions, review the schema conversion report before applying. |
| Redshift's Distribution Style and Sort Key affect performance but were hard to visualize as a newcomer. | Used the EXPLAIN plan to observe how queries actually execute and adjusted the Sort Key accordingly. |

### Lessons Learned:

* Creating separate Security Groups for EC2 and RDS and only allowing traffic from the EC2-SG into the RDS-SG is an important security pattern that ensures the database is never exposed directly to the internet.
* Hands-on backup/restore experience prepares for disaster recovery scenarios — not just creating a snapshot but also confirming the restore actually works.
* AWS DMS + SCT covers the full lifecycle of a real database migration project: from preparing the source database and converting the schema, to CDC migration, progress tracking, and error handling.
* Experience troubleshooting memory pressure and table errors in DMS helps prepare for issues commonly encountered in production environments.

### Next Week's Plan:

* Move on to AWS Data Analytics and NoSQL Services: Data Lake architecture and the data lifecycle (Ingest → Store → Catalog → Transform → Analyze → Visualize → Serve).
* Master Amazon DynamoDB from basics to advanced: data model, throughput mode, Secondary Index, Streams, Transactions, DAX, Global Tables, and design patterns.
* Learn the Kinesis ecosystem (Data Streams, Firehose, Data Analytics), AWS Glue (Data Catalog, ETL Jobs, DataBrew), and Amazon EMR.
* Learn Amazon Athena and Amazon QuickSight; practice 7 labs building an end-to-end data analytics pipeline.
