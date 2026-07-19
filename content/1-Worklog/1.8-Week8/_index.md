---
title: "Week 8 Worklog"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 1.8. </b> "
---

**Full Name:** Dinh Tuan Minh &emsp; | &emsp; **Student ID:** 2280601918

**Company Mentor:** Nguyen Gia Hung – Head of Solution Architect &emsp; | &emsp; **Academic Supervisor:** Vo Pham Thanh Luan

**Topic:** Final Project Proposal, Community Blog Post, and Attending an AWS Event

### Week 8 Objectives:

* Build a final project proposal that consolidates everything learned so far: a technology news collection and summarization system on a Serverless architecture.
* Write and share a technical blog post with the AWS Study Group VN community.
* Attend a First Cloud AI Journey community event to learn from real-world experience and expand a professional network.
* Transition from learning individual modules to the phase of applying consolidated knowledge into one complete product.

### Tasks to be carried out this week:
| Day | Task                                                                                                                                                                                                                    | Start Date | Completion Date | Reference Material                        |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ---------- | --------------- | ----------------------------------------- |
| 2   | - Final project proposal – Tech News Collection and Summarization System: overview, motivation, and Event-Driven Serverless architecture <br> - Identify the AWS services to use: Lambda (Collector/Processor/Serving), S3, DynamoDB, API Gateway, EventBridge Scheduler | 06/08/2026 | 06/08/2026      | <https://cloudjourney.awsstudygroup.com/> |
| 3   | - Design the data processing flow: ingestion flow, processing flow (with Amazon Bedrock), serving API flow <br> - Plan a 3-phase rollout: basic infrastructure (week 9), AI/API integration (week 10), finalization/demo (week 11) | 06/09/2026 | 06/09/2026      | <https://cloudjourney.awsstudygroup.com/> |
| 4   | - Write a technical blog post on AWS security and log auditing: building a CloudTrail → S3 → Glue Crawler → Athena pipeline <br> - Publish the post to the AWS Study Group VN Facebook community, with real query examples and a cost-optimization section | 06/10/2026 | 06/10/2026      | <https://cloudjourney.awsstudygroup.com/> |
| 5   | - Finalize and review the final project proposal <br> - Prepare content, questions, and background research on speakers for the First Cloud AI Journey Community Day event | 06/11/2026 | 06/11/2026      | <https://cloudjourney.awsstudygroup.com/> |
| 6   | - Review community feedback on the blog post, reply to comments and discussions <br> - Prepare mentally and gather materials for the Community Day event | 06/12/2026 | 06/12/2026      | <https://cloudjourney.awsstudygroup.com/> |
| 7   | - Attended the **First Cloud AI Journey Community Day** event in Ho Chi Minh City: <br>&emsp; + "From First Cloud AI Journey to AWS Partner" presentation <br>&emsp; + "A Scalable URL Shortening Service on AWS" presentation <br>&emsp; + "Real Stories on Culture at a Multinational Corporation" talk <br>&emsp; + Networking with the AWS Vietnam community and fellow FCJ trainees | 06/13/2026 | 06/13/2026      | First Cloud AI Journey Community Day event |

### Week 8 Achievements:

* Completed the "Tech News Collection and Summarization System" final project proposal: consolidating Lambda, S3, API Gateway, DynamoDB, and EventBridge knowledge into a complete serverless architecture, adding Amazon Bedrock for AI-powered summarization.
* Successfully wrote and published a blog post about CloudTrail, Athena, and Glue to the AWS Study Group VN community, reinforcing week 5's security knowledge by re-explaining it as a practical guide.
* Attended the Community Day event on 06/13/2026, learning from three different perspectives: a career journey from student to AWS Partner, real-world large-scale system design, and workplace culture at a multinational corporation.
* Networked directly with the AWS Vietnam community, met fellow FCJ trainees, received feedback on the final project idea, and kept up with industry trends.

### Challenges and Solutions:

| Challenge | Solution |
| --- | --- |
| Balancing features, complexity, and cost when designing the project proposal within the demo budget limit. | Referred to the AWS Pricing Calculator and prioritized serverless services (Lambda, DynamoDB on-demand) to optimize operating cost. |
| Explaining technical knowledge (CloudTrail, Athena) as a blog post accessible to a community with varying skill levels. | Structured the post clearly: problem statement → solution → step-by-step guide → real query examples → cost and optimization section. |
| First time attending a large-scale networking event, still a bit hesitant to talk with experienced professionals. | Proactively started conversations with other trainees and prepared questions for speakers in advance to make the most of the event. |

### Lessons Learned:

* The 8-step path from student to AWS Partner (Student Curiosity → Share Back) shows that a cloud career has a clear trajectory, and community contribution (writing blogs, attending events) is an essential part of the journey, not a side activity.
* The four system-design principles drawn from the URL Shortener project (Separation of Concerns, Defense at the Edge, Pre-computation over On-demand, Cache-aside Pattern) directly inspired the design of the final project's API serving layer.
* Technical skill is necessary but not sufficient; communication ability, professional culture, and business thinking are what distinguish a good engineer from one who delivers real value to an organization.
* Writing and sharing a blog post delivers value on two fronts: it reinforces knowledge through the act of explaining it, and it contributes to the community's knowledge ecosystem while building personal reputation.

### Next Week's Plan:

* Move into the detailed AWS infrastructure architecture design phase for the CloudBrief (Tech News Tracker & Summarizer) final project — a remote work week.
* Analyze and draw a complete architecture with 13 AWS services: EC2, CloudFront, S3, SQS, Bedrock, DynamoDB, EventBridge Scheduler, CloudWatch, SNS, IAM, Backup, Budgets, and SSM Parameter Store.
* Design a three-stage data pipeline via SQS (Collect → Extract → Summarize), a Dead-Letter Queue mechanism, and a retry contract for error handling.
* Analyze operating costs within the $200 AWS demo credit limit and design security following the Defense in Depth strategy.
