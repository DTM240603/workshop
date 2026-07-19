---
title: "Blog 1"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 3.1. </b> "
---

# Monitoring and Investigating S3 Security with AWS CloudTrail and Amazon Athena

**Author:** Dinh Tuan Minh &emsp; | &emsp; **Team:** ITSoldier

When a security incident happens on Amazon S3 — a batch of files gets deleted, an unfamiliar account downloads data, or access comes from an unknown IP — the first question is always: *"Who did this?"* Server access logs only tell you that a request happened, not who made it: which user, which role, whether MFA was enabled, or whether the request came from inside or outside the organization. Without this information, investigations become slow and compliance risk keeps rising.

AWS CloudTrail Data Events combined with Amazon Athena fill that gap, recording the full identity behind every S3 operation and letting you query millions of events in seconds without provisioning any infrastructure.

### 1. Solution Overview

This solution combines three AWS services to build a comprehensive S3 security investigation platform:

* **AWS CloudTrail Data Events:** Records every S3 API call (GetObject, PutObject, DeleteObject, etc.) along with full identity details: IAM user/role, MFA status, source IP, user agent, and cross-account access information. Unlike server access logs, which only capture HTTP-level details, CloudTrail answers "who did what" at the identity level.
* **Amazon S3 (Centralized Log Bucket):** Consolidates logs from multiple AWS accounts into a single bucket, organized by an account/region/date partition structure to optimize query costs later.
* **Amazon Athena with Partition Projection:** Lets you write SQL queries directly on JSON logs stored in S3 without any ETL or database. Partition projection automatically infers the folder structure, reducing the amount of data scanned and significantly cutting costs.

### 2. Core Benefits

* **Identity-based investigation:** Know exactly which IAM user, role, or federated identity performed an action, even in complex cross-account access or assume-role scenarios.
* **Anomaly detection:** Easily query for AccessDenied events, bulk file deletions, or access from unfamiliar IPs in seconds.
* **Compliance auditing:** Have complete evidence of who accessed sensitive data and when, supporting HIPAA, PCI DSS, or SOC 2 requirements.
* **Serverless, no infrastructure:** Athena automatically scales with the workload and only charges for the actual data scanned.

### 3. Implementation Guide

**Step 1 – Enable CloudTrail Data Events for S3:** In the CloudTrail Console, create a new trail (e.g., `s3-data-events-trail`). Choose a destination S3 bucket for the logs, enable SSE-KMS encryption and log file validation. Under Log events, uncheck Management events (to avoid duplicate charges if another trail already covers them) and select only Data events → S3. With Advanced event selectors, you can filter by bucket prefix or exclude low-value events like HeadObject to reduce cost.

**Step 2 – Consolidate logs into a single bucket:** If you have multiple AWS accounts, configure an Organization Trail from the Management Account with "Enable for all accounts in my organization." CloudTrail will automatically collect logs from all member accounts and deliver them to a central S3 bucket, organized as `AWSLogs/{organization_id}/{account_id}/CloudTrail/{region}/{year}/{month}/{day}/`.

**Step 3 – Create an Athena table with Partition Projection:** Create a database and table in Athena pointing to the S3 bucket holding the CloudTrail logs. Use Partition Projection so Athena automatically infers the account/region/date folder structure, eliminating the need to run `MSCK REPAIR TABLE` manually — queries will scan only the necessary partitions, cutting cost by up to 90% compared to a full scan.

**Step 4 – Analyze with SQL queries:** Once the table is set up, you can run practical investigation queries such as: finding all file deletions on a specific day, tracking a specific IAM user's activity, detecting access from outside the organization, or listing all AccessDenied events. An important best practice is to always filter by partition (account, region, date) before other conditions so Athena scans the minimum amount of data.

### 4. Conclusion

By combining CloudTrail Data Events to record full identity information with Amazon Athena for serverless querying, an organization can build a powerful S3 security investigation system without complex infrastructure. Every time someone touches data on S3 — whether uploading, downloading, or deleting — a clear trail is left with full identity information, ready to be investigated at any time.

**Original article:** [aws.amazon.com/blogs/storage/amazon-s3-audit-logging-part-2](https://aws.amazon.com/blogs/storage/amazon-s3-audit-logging-part-2-centralized-logging-and-analysis-of-s3-data-events-in-aws-cloudtrail-for-security-and-compliance/)

**Posted link on AWS Study Group VN:** [facebook.com/groups/awsstudygroupfcj/permalink/2183659809065646](https://www.facebook.com/groups/awsstudygroupfcj/permalink/2183659809065646/)

![Monitoring and investigating S3 security with CloudTrail and Athena](/images/3-BlogsPosted/3.1-Blog1/1.jpg)
