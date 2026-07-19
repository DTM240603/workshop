---
title: "Week 3 Worklog"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 1.3. </b> "
---

**Full Name:** Dinh Tuan Minh &emsp; | &emsp; **Student ID:** 2280601918

**Company Mentor:** Nguyen Gia Hung – Head of Solution Architect &emsp; | &emsp; **Academic Supervisor:** Vo Pham Thanh Luan

**Topic:** AWS Compute and Storage Services

### Week 3 Objectives:

* Master the architecture and configuration options of Amazon EC2: Instance Type, AMI, EBS, Instance Store, User Data, and EC2 Auto Scaling.
* Understand the role of extended storage services: Amazon EFS, FSx, Lightsail, and AWS MGN (Application Migration Service).
* Practice deploying and managing AWS Backup to build a data protection strategy.
* Set up hybrid storage with AWS Storage Gateway and deploy a static website on S3 integrated with CloudFront following security best practices.

### Tasks to be carried out this week:
| Day | Task                                                                                                                                                                                                                    | Start Date | Completion Date | Reference Material                        |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ---------- | --------------- | ----------------------------------------- |
| 2   | - Amazon EC2 – Instance Type: instance families (General Purpose, Compute/Memory/Storage Optimized, Accelerated Computing) <br> - AMI, Backup (EBS Snapshot), and Key Pair <br> - Amazon EBS: characteristics and volume types (gp3/gp2, io2/io1, st1, sc1) | 05/04/2026 | 05/04/2026      | <https://cloudjourney.awsstudygroup.com/> |
| 3   | - Instance Store: characteristics, data-loss scenarios, and suitable use cases <br> - EC2 User Data: bootstrapping mechanism, sample web server install script <br> - EC2 Auto Scaling: Launch Template, Auto Scaling Group, Scaling Policy types | 05/05/2026 | 05/05/2026      | <https://cloudjourney.awsstudygroup.com/> |
| 4   | - Extended services: Amazon EFS, Amazon FSx (Windows/Lustre/NetApp ONTAP), Amazon Lightsail, AWS MGN <br> - **Practice (Lab: AWS Backup):** <br>&emsp; + Deploy EC2/EBS infrastructure via CloudFormation <br>&emsp; + Create a Backup Plan, assign resources to back up <br>&emsp; + Test restore from a recovery point, clean up resources | 05/06/2026 | 05/06/2026      | <https://cloudjourney.awsstudygroup.com/> |
| 5   | - **Practice (Lab: S3 and Storage Gateway):** <br>&emsp; + Create an S3 bucket as the storage backend <br>&emsp; + Launch an EC2 instance simulating an on-premises gateway device <br>&emsp; + Activate and configure Storage Gateway connected to S3 <br>&emsp; + Create a File Share (SMB/NFS) so clients can mount and access data | 05/07/2026 | 05/07/2026      | <https://cloudjourney.awsstudygroup.com/> |
| 6   | - **Practice (Lab: S3 Static Website and Amazon CloudFront):** <br>&emsp; + Create an S3 bucket, upload static website content, enable Static Website Hosting <br>&emsp; + Configure a public Bucket Policy to test via the S3 endpoint <br>&emsp; + Block Public Access, create a CloudFront Distribution with Origin Access Control (OAC) <br>&emsp; + Practice S3 Lifecycle Policy and Cross-Region Replication (CRR) <br> - Consolidate knowledge, write the Week 3 report | 05/08/2026 | 05/08/2026      | <https://cloudjourney.awsstudygroup.com/> |

### Week 3 Achievements:

* Mastered the architecture and configuration options of Amazon EC2: Instance Type, AMI, EBS, Instance Store, User Data, Auto Scaling.
* Clearly understood the differences between storage types: EBS (durable block storage), Instance Store (high-speed ephemeral storage), EFS (shared file storage).
* Practiced deploying and managing AWS Backup, building a data protection strategy.
* Set up hybrid storage with AWS Storage Gateway, connecting on-premises infrastructure to AWS S3.
* Deployed a static website on S3 and integrated the CloudFront CDN following security best practices.
* Practiced Cross-Region Replication for a multi-region and disaster recovery strategy.
* Built an important foundation for designing cloud system architecture per the AWS Well-Architected Framework, especially the Reliability and Performance Efficiency pillars.

### Challenges and Solutions:

| Challenge | Solution |
| --- | --- |
| Many EBS Volume types (gp3, io2, st1, sc1) and Storage Classes were easy to confuse when choosing for each workload. | Built a comparison table by performance, IOPS, and cost criteria to select the right volume type for each use case. |
| Easy to confuse Instance Store and EBS regarding data durability. | Took clear notes on data-loss scenarios (stop, terminate, host failure) to avoid storing important data in the wrong place. |
| The process of configuring CloudFront + Origin Access Control (OAC) to block direct S3 access has many steps that are easy to get out of order. | Followed the lab sequence: enable Static Website → test via S3 endpoint → Block Public Access → configure OAC → retest via CloudFront. |

### Lessons Learned:

* Periodic restore testing is a critical part of a Business Continuity plan — not just creating backups, but confirming the backups are usable.
* AWS Storage Gateway allows on-premises infrastructure to blend seamlessly with the AWS cloud: local caching reduces latency while data is durably stored on S3.
* The S3 + CloudFront + OAC architecture is the standard pattern for deploying static websites and Single Page Applications on AWS, improving performance while strengthening S3 origin security.
* Cross-Region Replication is the foundation of a Multi-Region Availability strategy for applications requiring high availability.

### Next Week's Plan:

* Dive deeper into the AWS storage service ecosystem: Amazon S3 Access Point, advanced Storage Classes, and S3 Lifecycle Policy.
* Learn advanced S3 features: Static Website Hosting, CORS, access control layers (Bucket Policy, IAM Policy, ACL, Block Public Access, Pre-signed URL), and Amazon S3 Glacier.
* Learn about the AWS Snow Family for large-scale offline data migration, along with advanced AWS Storage Gateway and AWS Backup.
* Practice labs: AWS Backup with notifications, VM Import/Export, AWS Storage Gateway, Amazon FSx for Windows File Server, and a comprehensive S3 Static Website/CloudFront/Replication lab.
