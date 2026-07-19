---
title: "Week 4 Worklog"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 1.4. </b> "
---

**Full Name:** Dinh Tuan Minh &emsp; | &emsp; **Student ID:** 2280601918

**Company Mentor:** Nguyen Gia Hung – Head of Solution Architect &emsp; | &emsp; **Academic Supervisor:** Vo Pham Thanh Luan

**Topic:** AWS Storage Services

### Week 4 Objectives:

* Understand the overview of the AWS storage service ecosystem: Block Storage, File Storage, Object Storage, and hybrid/migration solutions.
* Master advanced Amazon S3 features: Access Point, Storage Classes, Lifecycle Policy, Static Website Hosting, CORS, and access control layers.
* Understand the role of the AWS Snow Family, AWS Storage Gateway, and AWS Backup in migration and hybrid cloud scenarios.
* Practice multiple labs covering backup, VM migration, hybrid storage, and standard AWS static content delivery.

### Tasks to be carried out this week:
| Day | Task                                                                                                                                                                                                                    | Start Date | Completion Date | Reference Material                        |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ---------- | --------------- | ----------------------------------------- |
| 2   | - Overview of AWS storage services: Block Storage, File Storage, Object Storage <br> - Amazon S3: overview, Access Point, and Storage Classes (Standard, Intelligent-Tiering, Standard-IA, One Zone-IA, Glacier...) and S3 Lifecycle Policy | 05/11/2026 | 05/11/2026      | <https://cloudjourney.awsstudygroup.com/> |
| 3   | - S3 Static Website Hosting and CORS <br> - S3 access control layers: Bucket Policy, IAM Policy, ACL, Block Public Access, Pre-signed URL <br> - Object Key, Prefix, and Performance; Multipart Upload; S3 Transfer Acceleration <br> - Amazon S3 Glacier: Instant/Flexible Retrieval, Deep Archive, Vault Lock | 05/12/2026 | 05/12/2026      | <https://cloudjourney.awsstudygroup.com/> |
| 4   | - AWS Snow Family (Snowcone, Snowball Edge, Snowmobile), AWS Storage Gateway, AWS Backup <br> - **Practice (Lab: AWS Backup – Backup and Restore):** <br>&emsp; + Create a Backup Plan with 7-day retention, assign resources by tag <br>&emsp; + Configure an SNS notification for backup job success/failure <br>&emsp; + Test restore from a recovery point <br> - **Practice (Lab: VM Import/Export):** <br>&emsp; + Export a VMware VM to OVA/VMDK, upload to S3 <br>&emsp; + Import it as an AMI and deploy an EC2 instance from it | 05/13/2026 | 05/13/2026      | <https://cloudjourney.awsstudygroup.com/> |
| 5   | - **Practice (Lab: AWS Storage Gateway):** <br>&emsp; + Deploy Storage Gateway (File Gateway) on EC2, activate via Console <br>&emsp; + Create an NFS/SMB File Share linked to an S3 bucket, mount it on an on-premises machine <br> - **Practice (Lab: Amazon FSx for Windows File Server):** <br>&emsp; + Create Multi-AZ FSx (SSD and HDD), create a file share and test performance <br>&emsp; + Enable Data Deduplication, Shadow Copies, User Storage Quotas; scale throughput/storage without downtime | 05/14/2026 | 05/14/2026      | <https://cloudjourney.awsstudygroup.com/> |
| 6   | - **Practice (Lab: S3 Static Website, CloudFront, and Replication):** <br>&emsp; + Create an S3 bucket, enable Static Website Hosting, test via the S3 endpoint <br>&emsp; + Block Public Access, configure CloudFront with Origin Access Control (OAC) <br>&emsp; + Enable S3 Versioning, use Lifecycle Policy to shift storage class over time <br>&emsp; + Configure Cross-Region Replication (CRR) for disaster recovery <br> - Consolidate knowledge, write the Week 4 report | 05/15/2026 | 05/15/2026      | <https://cloudjourney.awsstudygroup.com/> |

### Week 4 Achievements:

* Mastered Amazon S3: Access Point to simplify access management, Storage Classes to optimize cost, and Lifecycle Policy to automate data lifecycle.
* Deepened understanding of advanced S3 features: Static Website Hosting, CORS, multiple access control layers (Bucket Policy, IAM, ACL, Block Public Access, Pre-signed URL).
* Understood the role and use cases of S3 Glacier for cold storage and compliance archiving with Vault Lock.
* Clearly understood the AWS Snow Family as a large-scale offline data migration solution — important when network bandwidth is the bottleneck.
* Practiced deploying AWS Storage Gateway to connect on-premises infrastructure with S3, creating seamless hybrid cloud storage.
* Practiced the entire VM Import/Export process — the foundation of a lift-and-shift migration strategy.
* Mastered Amazon FSx for Windows: from Multi-AZ deployment to enterprise features like deduplication, shadow copies, quotas, and dynamic scaling.
* Built a standard AWS static content delivery architecture with S3 + CloudFront + OAC; combined Versioning, Lifecycle, and Cross-Region Replication for a multi-layered data protection strategy.

### Challenges and Solutions:

| Challenge | Solution |
| --- | --- |
| The many S3 Storage Classes (7 types) were easy to confuse regarding cost and retrieval time. | Built a comparison table by storage cost, retrieval fee, and retrieval time to choose the right class for each data type. |
| Configuring S3 Access Points for multiple teams/VPCs sharing one bucket was still quite new. | Practiced with specific use cases: one dedicated Access Point per user group with a simpler policy instead of one complex bucket policy. |
| The VM Import/Export process has many steps (export OVA/VMDK, upload to S3, import AMI, deploy) that were easy to get wrong in format or S3 permissions. | Followed the lab's sequential checklist step by step, carefully checking the S3 bucket ACL configuration before exporting/importing. |

### Lessons Learned:

* SNS notifications are especially important in production to detect backup failures promptly; cross-account backup is a best practice to protect backup data from incidents in the primary account.
* VM Import/Export is the foundation of a lift-and-shift migration strategy: the real-world process is not just copying data but also involves format conversion, S3 permission configuration, and compatibility checks.
* Storage Gateway shows how AWS solves hybrid cloud storage in practice: local caching ensures performance for hot data, while the S3 backend ensures durability and scalability.
* FSx's ability to scale throughput and storage without downtime is a significant advantage over traditional physical NAS/SAN.
* The S3 + CloudFront + OAC architecture is the standard pattern for deploying Single Page Applications and static content on AWS; S3 Versioning combined with Lifecycle Policy and CRR creates a comprehensive data protection strategy across multiple dimensions: version, lifecycle, and geography.

### Next Week's Plan:

* Move on to Security and Identity Management on AWS: the Shared Responsibility Model between AWS and the customer.
* Study AWS IAM in depth (User, Group, Role, Policy), Amazon Cognito, AWS Organization and Service Control Policy, and AWS Identity Center (SSO).
* Learn Amazon KMS (Key Management Service) and AWS Security Hub for centralized security monitoring.
* Practice labs on Security Hub, EC2 automation with Lambda, Tag/Resource Group management, advanced IAM (Switch Role, Tag-Based Access Control), KMS/CloudTrail/Athena, and comparing IAM Access Key with IAM Role.
