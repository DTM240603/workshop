---
title: "Week 10 Worklog"
date: 2024-01-01
weight: 2
chapter: false
pre: " <b> 1.10. </b> "
---

**Full Name:** Dinh Tuan Minh &emsp; | &emsp; **Student ID:** 2280601918

**Company Mentor:** Nguyen Gia Hung – Head of Solution Architect &emsp; | &emsp; **Academic Supervisor:** Vo Pham Thanh Luan

**Topic:** Team Task Assignment and Kicking Off CloudBrief Implementation

### Week 10 Objectives:

* Apply a professional workflow using GitHub Issues to assign and track progress on the CloudBrief team project.
* Clearly understand the scope and Definition of Done for the assigned task: Deploy CloudBrief to AWS and collect evidence.
* Learn AWS CDK (Cloud Development Kit) as the Infrastructure as Code tool to prepare for project deployment.
* Track and coordinate with teammates completing the core implementation, QA, frontend, and data pipeline workstreams.

### Tasks to be carried out this week:
| Day | Task                                                                                                                                                                                                                    | Start Date | Completion Date | Reference Material                        |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ---------- | --------------- | ----------------------------------------- |
| 2   | - Overview of Week 10 activities: the ITSoldier team agreed to use GitHub Issues for task assignment (Assignee, Deadline, Scope, "Done when") <br> - Tracked Issue #1, "Core CloudBrief implementation: CDK, API, security, integration," completed and closed by a teammate | 06/22/2026 | 06/22/2026      | ITSoldier team GitHub repository |
| 3   | - Studied the details of other members' assignments: Issue #3 (API QA, Security Checks, Regression Tests), Issue #4 (Read-only CloudBrief Dashboard Frontend), Issue #5 (News Collection, Extraction, and Summarization Pipeline) | 06/23/2026 | 06/23/2026      | ITSoldier team GitHub repository |
| 4   | - Received Issue #2, "Deploy CloudBrief to AWS and collect evidence" (deadline 07/05–07/10/2026) <br> - Defined the detailed scope: personal AWS account preparation, CDK bootstrap/deploy, deployed smoke tests, evidence capture, cleanup | 06/24/2026 | 06/24/2026      | TEAM_TASK_SPLIT-cloudbrief.md document |
| 5   | - Learned AWS CDK: App and Stack concepts, the three levels of Constructs (L1/L2/L3), CDK Bootstrap <br> - Learned the cdk synth, cdk diff, cdk deploy, and cdk destroy commands; compared CDK with plain CloudFormation YAML and Terraform | 06/25/2026 | 06/25/2026      | AWS CDK documentation |
| 6   | - Practiced reading and analyzing a sample CDK code snippet (S3 bucket + CloudFront with Origin Access Control) <br> - Clearly defined the 5 Definition of Done criteria for Issue #2 <br> - Consolidated knowledge, wrote the Week 10 report | 06/26/2026 | 06/26/2026      | AWS CDK documentation |

### Week 10 Achievements:

* Completed team task assignment: all 5 main project tasks were clearly assigned with an Assignee, Deadline, and specific Scope via GitHub Issues.
* Recorded a major step forward from a teammate: Issue #1 (Core implementation: CDK, API, security, integration) was closed — an essential codebase foundation for the whole team to deploy and test against.
* Fully understood the deploy task (Issue #2): grasped the entire scope, from AWS account preparation and CDK bootstrap/deploy to smoke testing, evidence collection, and post-demo cleanup, with a clear Definition of Done comprising 5 measurable criteria.
* Learned AWS CDK hands-on: first exposure to and application of this important Infrastructure as Code tool, combining programming skills with AWS knowledge.
* Applied a professional workflow: GitHub Issues + Definition of Done, similar to real startup and enterprise environments.

### Challenges and Solutions:

| Challenge | Solution |
| --- | --- |
| First time using AWS CDK, not yet familiar with the Python/TypeScript syntax for defining infrastructure. | Read a teammate's sample code from Issue #1 and practiced with a small example (S3 + CloudFront OAC) before tackling the full stack deployment. |
| Clearly scoping and defining completion criteria for an operations/deployment task (as opposed to a feature-coding task) was fairly new. | Referred to the team's TEAM_TASK_SPLIT-cloudbrief.md document and clarified the Definition of Done with 5 specific, evidence-backed criteria. |
| The project's overall deadline was fairly tight (07/05–07/10/2026), while deployment had to wait for Issue #1 to be completed first. | Proactively studied AWS CDK in advance and prepared the AWS account (Budgets, SSM Parameter) in parallel while waiting for the codebase to be finished. |

### Lessons Learned:

* Completing Issue #1 was a major breakthrough: having a complete codebase to deploy reduces dependency and integration risk in the final stage of the project.
* A clear Definition of Done with measurable criteria reflects Agile/Scrum principles, avoiding the "thought it was done but it wasn't" situation common in student team projects.
* AWS CDK allows infrastructure to be defined with a real programming language, reused via Constructs, and is far more concise and easier to review than writing plain CloudFormation YAML.
* The GitHub Issues + Definition of Done + clear completion criteria workflow is valuable project management experience, similar to a real enterprise work environment.

### Next Week's Plan:

* Begin directly executing the deploy task: prepare a personal AWS account, configure the AWS CLI and AWS Budgets.
* Run CDK bootstrap, review the teammate's CDK stack code, perform cdk synth/diff, and run cdk deploy --all to deploy all 12 AWS services in the stack.
* Run post-deploy smoke tests (health check, dashboard, API, admin endpoint protection, S3 security check) and collect deployment evidence per AWSFCAJ requirements.
* Coordinate with other teammates finishing the frontend dashboard, the data processing pipeline, and the QA/security check suite, working toward a complete demo before 07/10/2026.
