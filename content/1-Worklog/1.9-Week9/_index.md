---
title: "Week 9 Worklog"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 1.9. </b> "
---

**Full Name:** Dinh Tuan Minh &emsp; | &emsp; **Student ID:** 2280601918

**Company Mentor:** Nguyen Gia Hung – Head of Solution Architect &emsp; | &emsp; **Academic Supervisor:** Vo Pham Thanh Luan

**Topic:** Designing the AWS Infrastructure Architecture for the CloudBrief Final Project

### Week 9 Objectives:

* Design a complete AWS architecture for the CloudBrief final project, applying everything learned from Week 3 through Week 8.
* Analyze trade-offs between architectural choices (Lambda vs. EC2, API Gateway vs. an EC2 API server, NAT Gateway vs. Public Subnet) based on cost, operations, and security.
* Design an asynchronous data pipeline via Amazon SQS with a clear Dead-Letter Queue mechanism and retry contract.
* Build a Defense in Depth security strategy and a cost-control plan within the $200 AWS demo credit limit.

### Tasks to be carried out this week:
| Day | Task                                                                                                                                                                                                                    | Start Date | Completion Date | Reference Material                        |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ---------- | --------------- | ----------------------------------------- |
| 2   | - Introduce the CloudBrief project (Tech News Tracker & Summarizer): name, context, and project goals <br> - Identify the 13 AWS services to use: EC2, CloudFront, S3, SQS, Bedrock, DynamoDB, EventBridge Scheduler, CloudWatch, SNS, IAM, Backup, Budgets, SSM Parameter Store | 06/15/2026 | 06/15/2026      | ITSoldier team design document |
| 3   | - Design the Frontend Delivery layer: Amazon CloudFront with Origin Access Control (OAC), S3 Frontend Bucket with Block Public Access <br> - Design the EC2 Application layer: API server, admin endpoints protected by an API key, mandatory IMDSv2, Auto Scaling Group for Host Recovery | 06/16/2026 | 06/16/2026      | ITSoldier team design document |
| 4   | - Design the Ingestion & Schedule layer: RSS/Hacker News API data sources, collection schedule via systemd timer/EventBridge Scheduler <br> - Design the Managed Data & AI Pipeline: a 3-stage pipeline via SQS (Collect → Extract → Summarize) with Amazon Bedrock Nova Lite <br> - Design the Dead-Letter Queue and Retry Contract for error handling (CONTENT_FAILED, SUMMARY_FAILED, SUMMARIZED_PARTIAL) | 06/17/2026 | 06/17/2026      | ITSoldier team design document |
| 5   | - Design the Monitoring & Security layer: CloudWatch Logs/Metrics/Alarms, SNS Email Alert Fanout <br> - Design the Security/Recovery/Cost Controls layer: IAM Least Privilege, AWS Backup, AWS Budgets (four alert thresholds at $50/$100/$150/$180) <br> - Draw the end-to-end data flow: the dashboard-viewing flow and the news collection/processing flow | 06/18/2026 | 06/18/2026      | ITSoldier team design document |
| 6   | - Analyze operating costs: comparing an EC2-first configuration ($20.30/month) against a configuration with an ALB ($42.56/month) <br> - Analyze the Defense in Depth security design (Edge, Network, Application, Identity, Data) and XSS prevention <br> - Consolidate lessons learned, finalize the architecture diagram and the CloudBrief project introduction slides <br> - Consolidate knowledge, write the Week 9 report | 06/19/2026 | 06/19/2026      | ITSoldier team design document |

### Week 9 Achievements:

* Designed a real-world AWS architecture: for the first time, applied all knowledge accumulated from Weeks 3–8 into a complete system design coordinating 13 AWS services, balancing features, complexity, and cost within the $200 budget.
* Analyzed architectural trade-offs: gained deeper understanding of real-world trade-offs between Lambda vs. EC2, API Gateway vs. an EC2 API server, and NAT Gateway vs. Public Subnet with a Security Group.
* Mastered pipeline design with SQS: how to use SQS to build a highly fault-tolerant asynchronous pipeline with a clear DLQ and retry contract.
* Applied a Defense in Depth security architecture to a real system: from the CloudFront edge, Security Group network layer, API Key application layer, to the IAM identity layer and data encryption.
* Practiced cost engineering thinking: every architectural decision includes a cost estimate — a skill with high real-world value in enterprise environments.

### Challenges and Solutions:

| Challenge | Solution |
| --- | --- |
| Balancing features, complexity, and cost within the $200 AWS demo credit limit. | Applied a "Cost-First" mindset: evaluating cost right when choosing a service instead of calculating it after the design was finished. |
| Designing the retry contract and Dead-Letter Queue for a 3-stage pipeline was fairly complex when first approached. | Clearly defined each error type (CONTENT_FAILED, SUMMARY_FAILED, SUMMARIZED_PARTIAL) and the corresponding retry path for each. |
| With no hands-on lab this week, it was hard to validate the design immediately. | Cross-checked against the AWS Well-Architected Framework documentation and discussed with the mentor to challenge and refine the design. |

### Lessons Learned:

* "Cost-First" design thinking: every decision about a service and its configuration must be evaluated for cost from the start. Removing the NAT Gateway and API Gateway and choosing EC2 t4g ARM over x86 extended the runway from ~5 months to ~10 months within the same $200 budget.
* SQS acts as the "glue" of the pipeline architecture: each stage can retry independently, the DLQ provides an automatic safety net, and SQS visibility timeout naturally prevents duplicate processing.
* A fallback strategy matters for a demo: a demo system must always "keep working" even when an external service has an outage — the fallback summary ensures the pipeline isn't blocked when Bedrock fails.
* Mandatory IMDSv2 and never hardcoding credentials are direct lessons from the IAM/KMS/SSM best practices learned in Week 5, eliminating the risk of credential leaks entirely.

### Next Week's Plan:

* Move from the design phase into actual implementation of the CloudBrief project, using GitHub Issues for transparent team task assignment.
* Receive and clearly understand the assigned task scope: preparing a personal AWS account, CDK bootstrap/deploy, smoke testing, and collecting deployment evidence.
* Learn AWS CDK (Cloud Development Kit) as the Infrastructure as Code tool for deploying all 13 AWS services from a Python/TypeScript codebase.
* Track progress from other team members: core implementation (CDK/API/security), QA & security checks, the frontend dashboard, and the news collection/summarization pipeline.
