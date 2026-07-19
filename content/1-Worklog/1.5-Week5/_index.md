---
title: "Week 5 Worklog"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 1.5. </b> "
---

**Full Name:** Dinh Tuan Minh &emsp; | &emsp; **Student ID:** 2280601918

**Company Mentor:** Nguyen Gia Hung – Head of Solution Architect &emsp; | &emsp; **Academic Supervisor:** Vo Pham Thanh Luan

**Topic:** Security and Identity Management on AWS

### Week 5 Objectives:

* Understand the Shared Responsibility Model between AWS and the customer.
* Master AWS IAM: User, Group, Role, Policy, and advanced techniques such as Tag-Based Access Control, Permission Boundary, and IAM Condition.
* Distinguish Amazon Cognito from IAM; understand AWS Organization, Service Control Policy, and AWS Identity Center for multi-account governance.
* Practice Amazon KMS for data encryption and AWS Security Hub for centralized security monitoring through hands-on labs.

### Tasks to be carried out this week:
| Day | Task                                                                                                                                                                                                                    | Start Date | Completion Date | Reference Material                        |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ---------- | --------------- | ----------------------------------------- |
| 2   | - Shared Responsibility Model: "Security OF the Cloud" (AWS) and "Security IN the Cloud" (customer) <br> - AWS IAM: User, Group, Role, Policy; policy evaluation (implicit deny → explicit allow → explicit deny) <br> - IAM Best Practices: MFA, Least Privilege, IAM Role instead of Access Key, IAM Access Analyzer | 05/18/2026 | 05/18/2026      | <https://cloudjourney.awsstudygroup.com/> |
| 3   | - Amazon Cognito: User Pools (authentication) and Identity Pools (federated identities) <br> - AWS Organization: Management Account, Organizational Unit, Member Account, Service Control Policy (SCP) <br> - AWS Identity Center (SSO): Permission Set, integration with Active Directory/Okta/Azure AD | 05/19/2026 | 05/19/2026      | <https://cloudjourney.awsstudygroup.com/> |
| 4   | - Amazon KMS: AWS Managed Key, Customer Managed Key, AWS Owned Key; Envelope Encryption, Key Policy, Automatic Key Rotation <br> - AWS Security Hub: aggregating findings, Security Score, compliance standards <br> - **Practice (Lab: Security Hub):** enable, evaluate Security Score, analyze failed controls <br> - **Practice (Lab: Tag and Resource Group Management):** assign/edit/filter tags, create a Resource Group | 05/20/2026 | 05/20/2026      | <https://cloudjourney.awsstudygroup.com/> |
| 5   | - **Practice (Lab: EC2 Automation with Lambda and Slack Webhook):** create VPC/SG/EC2, IAM Role for Lambda, scheduled start/stop via EventBridge, Slack notifications <br> - **Practice (Lab: Advanced IAM – Switch Role and Tag-Based Access Control):** IAM Policy with a ResourceTag Condition, Switch Role, testing AccessDenied <br> - **Practice (Lab: IAM – Limiting User Permissions):** Restriction Policy, testing allowed/denied actions <br> - **Practice (Lab: IAM Switch Role Limited by IP and Time):** Condition aws:SourceIp and aws:CurrentTime | 05/21/2026 | 05/21/2026      | <https://cloudjourney.awsstudygroup.com/> |
| 6   | - **Practice (Lab: KMS, CloudTrail, and Amazon Athena):** create a Customer Managed Key, encrypt S3 (SSE-KMS), enable CloudTrail, query logs with SQL via Athena <br> - **Practice (Lab: IAM Access Key vs. IAM Role):** compare long-term credentials and temporary credentials for EC2 access to S3 <br> - Consolidate knowledge, write the Week 5 report | 05/22/2026 | 05/22/2026      | <https://cloudjourney.awsstudygroup.com/> |

### Week 5 Achievements:

* Mastered the Shared Responsibility Model — the foundation of cloud security thinking, clearly defining the boundary of responsibility between AWS and the customer.
* Gained deep understanding of AWS IAM: User, Group, Role, Policy, and advanced techniques such as TBAC, Permission Boundary, IAM Condition, and Switch Role.
* Distinguished Amazon Cognito (identity for application end-users) from IAM (identity for AWS resources) — two services often confused.
* Learned AWS Organization and SCP as account-level permission governance solutions, the foundation of enterprise multi-account architecture.
* Understood AWS Identity Center as a centralized SSO solution for environments with many AWS accounts and SaaS applications.
* Mastered Amazon KMS: distinguishing AWS Managed Key from Customer Managed Key, understanding Key Policy and Envelope Encryption mechanisms.
* Practiced AWS Security Hub as a "glass pane" that aggregates security findings and measures compliance against standard frameworks.
* Practiced 8 comprehensive labs: from security monitoring, data encryption, and audit logging to secure automation and proper credential management.

### Challenges and Solutions:

| Challenge | Solution |
| --- | --- |
| Easy to confuse Identity-based Policy, Resource-based Policy, Permission Boundary, and Service Control Policy (SCP). | Built a comparison table of scope: attached to identity or resource, applied at the account or Organization level. |
| The many KMS Key types (AWS Managed, Customer Managed, AWS Owned) were easy to confuse regarding management rights and cost. | Took notes on the characteristics, rotation capability, and cost of each key type to select the right one for each need. |
| IAM Policy evaluation logic (explicit deny/allow/implicit deny) became quite complex when testing many labs in a row. | Used the IAM Policy Simulator to test policies before actual deployment. |

### Lessons Learned:

* Even a newly created AWS account already had many Security Hub findings due to missing MFA, CloudTrail, or basic security settings.
* The Lambda + EventBridge Scheduler pattern is a common cost optimization solution that can significantly reduce EC2 costs by shutting down instances outside working hours.
* Tagging is an important cloud governance discipline: it not only helps organize resources but is also the basis for conditional IAM Policies, Cost Allocation Reports, and automation.
* Tag-Based Access Control (TBAC) is the foundation for IAM strategy in enterprise environments where manually managing policies for each resource is infeasible.
* Explicit Deny always wins over any Allow, while the absence of an Allow means Implicit Deny — the ability to write and test IAM policies accurately is an essential skill.
* KMS (data encryption), CloudTrail (audit logging), and Athena (log analysis) form the pillars of a Data Security and Security Monitoring strategy on AWS.
* IAM Condition (limiting by IP, by time) is a practical Zero Trust technique that prevents abuse of stolen credentials outside a controlled environment.
* IAM Role uses automatically rotating temporary credentials and is always recommended over Access Key (long-term credentials) for EC2, Lambda, and every compute service.

### Next Week's Plan:

* Move on to AWS Database Services: review foundational concepts (SQL vs NoSQL, ACID vs BASE, OLTP vs OLAP).
* Learn Amazon RDS (architecture, Multi-AZ, Read Replica, backup/PITR) and Amazon Aurora (distributed storage architecture, Aurora Cluster, Serverless v2, Global Database).
* Learn Amazon Redshift (data warehouse, MPP, Redshift Spectrum) and Amazon ElastiCache (Redis, Memcached, caching patterns).
* Practice deploying a 3-tier architecture with RDS in a private subnet, and practice the full database migration process with AWS Database Migration Service (DMS) combined with the Schema Conversion Tool (SCT).
