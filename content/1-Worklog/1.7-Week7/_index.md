---
title: "Week 7 Worklog"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 1.7. </b> "
---

**Full Name:** Dinh Tuan Minh &emsp; | &emsp; **Student ID:** 2280601918

**Company Mentor:** Nguyen Gia Hung – Head of Solution Architect &emsp; | &emsp; **Academic Supervisor:** Vo Pham Thanh Luan

**Topic:** AWS Data Analytics and NoSQL Services

### Week 7 Objectives:

* Understand Data Lake architecture on AWS and the data lifecycle: Ingest → Store → Catalog → Transform → Analyze → Visualize → Serve.
* Master Amazon DynamoDB from basics to advanced: data model, Secondary Index, Streams, Transactions, DAX, Global Tables, and design patterns.
* Understand the AWS streaming and ETL ecosystem: Amazon Kinesis, AWS Glue, and Amazon EMR.
* Master Amazon Athena for serverless SQL query and Amazon QuickSight for data visualization; practice building an end-to-end data analytics pipeline.

### Tasks to be carried out this week:
| Day | Task                                                                                                                                                                                                                    | Start Date | Completion Date | Reference Material                        |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ---------- | --------------- | ----------------------------------------- |
| 2   | - Overview of Data Lake on AWS and the data lifecycle (Ingest, Store, Catalog, Transform, Analyze, Visualize, Serve) <br> - Amazon DynamoDB: data model (Table/Item/Attribute), Partition Key/Sort Key, Global/Local Secondary Index, throughput mode (Provisioned/On-Demand), Streams, Transactions, DAX, Global Tables, design patterns | 06/01/2026 | 06/01/2026      | <https://cloudjourney.awsstudygroup.com/> |
| 3   | - Amazon Kinesis: Data Streams, Data Firehose, Data Analytics <br> - AWS Glue: Data Catalog, Crawler, ETL Jobs, DynamicFrame, Interactive Sessions, Workflows, Glue DataBrew <br> - Amazon EMR: cluster architecture, EMR Serverless, EMR on EKS | 06/02/2026 | 06/02/2026      | <https://cloudjourney.awsstudygroup.com/> |
| 4   | - Amazon Athena: serverless SQL query on S3, Federated Query, Workgroups <br> - Amazon QuickSight: SPICE, Data Sources, Analyses/Dashboards, ML Insights <br> - **Practice (Lab: Data Analytics Pipeline with Kinesis, Glue, Athena, and QuickSight):** create a Firehose Delivery Stream, a Glue Crawler, query with Athena, visualize with QuickSight | 06/03/2026 | 06/03/2026      | <https://cloudjourney.awsstudygroup.com/> |
| 5   | - **Practice (Lab: DynamoDB from Basics to Advanced):** basic CRUD, backup/PITR, Single Table Design, GSI Overloading, Global Tables, DynamoDB Streams + Lambda <br> - **Practice (Lab: Redshift – Cost Analysis and Advanced Queries):** loading data, Distribution Style, cost allocation tags, EXPLAIN plan <br> - **Practice (Lab: Accessing DynamoDB via CloudShell, Console, and SDK)** <br> - **Practice (Lab: AWS Glue DataBrew):** data profiling, cleaning, and standardizing data | 06/04/2026 | 06/04/2026      | <https://cloudjourney.awsstudygroup.com/> |
| 6   | - **Practice (Lab: Data Lake End-to-End Pipeline):** ingest/store via a 3-zone S3, catalog with Lake Formation, transform via Glue Interactive/GUI/DataBrew/EMR, analyze with Athena/Kinesis Data Analytics, serve via Lambda, warehouse on Redshift <br> - **Practice (Lab: Building a Dashboard with Amazon QuickSight):** basic dashboard, conditional formatting, interactive dashboard with Filter/Action <br> - Consolidate knowledge, write the Week 7 report | 06/05/2026 | 06/05/2026      | <https://cloudjourney.awsstudygroup.com/> |

### Week 7 Achievements:

* Understood Data Lake architecture on AWS: S3 as the center, a data pipeline following the lifecycle Ingest → Store → Catalog → Transform → Analyze → Visualize → Serve.
* Mastered Amazon DynamoDB from basics to advanced: data model, throughput mode, Secondary Index, Streams, Transactions, DAX, Global Tables, and real-world design patterns.
* Understood the Amazon Kinesis ecosystem: Data Streams (custom consumer), Firehose (managed delivery), Data Analytics (real-time SQL/Flink).
* Learned AWS Glue: Data Catalog and Crawler, Glue ETL, Interactive Sessions, Workflows.
* Practiced AWS Glue DataBrew for visual data preparation: profiling, cleaning, and transformation without code.
* Understood Amazon EMR for big data processing requiring high customization with Apache Spark/Hadoop on a managed cluster.
* Mastered Amazon Athena: serverless SQL query directly on S3, cost optimization with Parquet and partitioning, Federated Query.
* Practiced building a professional dashboard with Amazon QuickSight: from static visualizations to an interactive dashboard with filters and actions.
* Completed 7 hands-on labs, especially the end-to-end Data Lake pipeline lab — the most comprehensive multi-service lab.

### Challenges and Solutions:

| Challenge | Solution |
| --- | --- |
| DynamoDB schema design is completely different from a relational database, making it hard to think about access patterns before designing the schema. | Practiced specific design patterns: Single Table Design, Adjacency List Pattern, Write Sharding, and Sparse Index. |
| The many ETL tools (Glue ETL, DataBrew, EMR) were easy to confuse regarding which tool to use when. | Compared by criteria: Glue ETL (batch, code-first), DataBrew (no-code, data quality), EMR (large-scale, custom framework), Athena (ad-hoc query). |
| The end-to-end Data Lake pipeline lab has many steps and services, making it easy to lose track while practicing. | Followed a sequential checklist: Ingest → Store → Catalog → Transform → Analyze → Serve → Visualize, verifying results at each step before moving to the next. |

### Lessons Learned:

* The S3 → Firehose → Glue Crawler → Athena → QuickSight architecture is the most common pattern for analytics use cases, with low cost thanks to being serverless and requiring no infrastructure management.
* The most important principle when designing DynamoDB is "know the access pattern before designing the schema" — completely different from relational database thinking.
* Tag-based cost allocation is an important best practice for accurately allocating cloud costs to each team/project, especially with Redshift.
* AWS Glue DataBrew solves one of the biggest bottlenecks in a data project: most of the time is usually spent on data cleaning; the Data Profile report helps avoid "garbage in, garbage out."
* There is no single tool suited to every data analytics problem — choosing the right tool for the right problem is an important skill for a Data Engineer.
* Interactive dashboards in QuickSight let users explore data on their own, reducing dependence on the data team for every reporting request.

### Next Week's Plan:

* Propose and present the team's final project based on the foundation of Compute, Storage, Security, Database, and Analytics knowledge learned over 7 weeks.
* Write and publish a knowledge-sharing blog post to the AWS Study Group VN community.
* Attend a community event organized by First Cloud AI Journey to network, learn from real-world experience, and expand professional connections.
