---
title: "Week 11 Worklog"
date: 2024-01-01
weight: 2
chapter: false
pre: " <b> 1.11. </b> "
---

**Full Name:** Dinh Tuan Minh &emsp; | &emsp; **Student ID:** 2280601918

**Company Mentor:** Nguyen Gia Hung – Head of Solution Architect &emsp; | &emsp; **Academic Supervisor:** Vo Pham Thanh Luan

**Topic:** Deploying CloudBrief to AWS and Collecting Deployment Evidence (GitHub Issue #2)

### Week 11 Objectives:

* Execute the exact scope of Issue #2 "Deploy CloudBrief to AWS and collect evidence": AWS account preparation, CDK bootstrap/deploy, EC2 configuration, testing against the deployed environment, and evidence collection.
* Verify that the CloudBrief system works correctly on a real AWS account (not just from source code or local CDK output).
* Confirm that the security controls designed earlier (mandatory IMDSv2, a CloudFront-restricted Security Group, S3 Block Public Access, an API key stored only as a hash in SSM) are actually in effect on the deployed environment.
* Collect complete deployment evidence per AWSFCAJ requirements to support the final internship report.

### Tasks to be carried out this week:
| Day | Task                                                                                                                                                                                                                    | Start Date | Completion Date | Reference Material                        |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ---------- | --------------- | ----------------------------------------- |
| 2   | - Carefully read Issue #2 (scope, security checklist, Definition of Done) and the `TEAM_TASK_SPLIT-cloudbrief.md`/`CLOUDBRIEF_EC2_AGENT_SPEC.md` documents <br> - Prepare the AWS account: create a dedicated IAM user for deployment, configure the AWS CLI for `us-east-1`, verify Bedrock access for `amazon.nova-lite-v1:0`, prepare `DEMO_API_KEY` and `BUDGET_EMAIL` | 06/29/2026 | 06/29/2026      | TEAM_TASK_SPLIT-cloudbrief.md |
| 3   | - Ran `bun install`, `bun run build`, `bun run test`, and `bun run cdk synth` locally to confirm there were no errors before deploying <br> - Reviewed the teammate's CDK stack code (Issue #1: core implementation) to understand exactly which resources would be created | 06/30/2026 | 06/30/2026      | CLOUDBRIEF_EC2_AGENT_SPEC.md |
| 4   | - Verified AWS CLI credentials (`aws sts get-caller-identity`), ran `cdk bootstrap` and `cdk deploy --require-approval never` <br> - Configured EC2 via AWS SSM Run Command: resolved a `curl-minimal` package conflict on Amazon Linux 2023, installed the Bun runtime, created the environment file, installed the Nginx reverse proxy, built and uploaded the app bundle, enabled the systemd services <br> - Ran the first smoke test (`/health`, `/articles`, `/collect` with/without an API key) | 07/01/2026 | 07/01/2026      | docs/operations.md |
| 5   | - Found and fixed an Nginx routing bug for `/api/v1` (Nginx stripped the `/api/` prefix while Express mounted the v1 router at `/api/v1`) <br> - Ran end-to-end pipeline testing: triggered `/collect`, confirmed articles moved through all 3 stages (Collect → Extract → Summarize) and appeared via CloudFront <br> - Collected deployment evidence: screenshots of the CDK deploy, CloudFront, EC2, DynamoDB, S3, CloudWatch Logs/Alarms, SNS, and AWS Budget | 07/02/2026 | 07/02/2026      | docs/operations.md |
| 6   | - Reviewed the Issue #2 security checklist: confirmed mandatory IMDSv2, the EC2 Security Group only accepting traffic from CloudFront, both S3 buckets with Block Public Access enabled, the API key stored only as a SHA-256 hash in SSM SecureString, and no admin policy attached to the EC2 Instance Role <br> - Consolidated all evidence against the 5 Definition of Done criteria and wrote up the deployment report | 07/03/2026 | 07/03/2026      | Issue #2 – Deploy CloudBrief to AWS |
| 7   | - Attended the **"Amazon Web Services (AWS): Enterprise Cloud Architectures and Industry Applications – Featuring Cloud Kinetics & Renova Cloud"** event at the AWS Office, Bitexco Tower: 4 talks on the Cloud/Data hiring market, real-world Data Engineer experience, soft skills, and an AI mindset for Freshers <br> - Networked with the AWS Vietnam community | 07/04/2026 | 07/04/2026      | AWS Enterprise Cloud Architectures event |

### Week 11 Achievements:

* Successfully deployed the entire CloudBrief infrastructure to a real AWS account via `cdk deploy`, with no resource left in a ROLLBACK/FAILED state.
* Got EC2 running stably with the API server and worker process managed by systemd, overcoming the initial cloud-init failure by completing the setup manually via SSM Run Command.
* Confirmed both the dashboard and API were reachable over CloudFront HTTPS; smoke tests and end-to-end pipeline testing both passed (Collect → Extract → Summarize → visible on the dashboard).
* Verified that the security controls designed back in Week 9 were actually in effect on the deployed environment (IMDSv2, CloudFront-restricted Security Group, S3 Block Public Access, API key hash in SSM).
* Collected complete deployment evidence (screenshots of CloudFormation, CloudFront, EC2, DynamoDB, S3, CloudWatch, SNS, Budget), satisfying 4 of the 5 Definition of Done criteria for Issue #2.
* Attended an AWS event on enterprise architecture and the hiring market, gaining a real-world perspective for positioning the CloudBrief project in future interviews.

### Challenges and Solutions:

| Challenge | Solution |
| --- | --- |
| The automatic cloud-init script failed due to a conflict with the pre-installed `curl-minimal` package on Amazon Linux 2023, preventing the application from installing automatically on EC2. | Used AWS Systems Manager (SSM) Run Command to run `dnf install -y --allowerasing curl unzip amazon-cloudwatch-agent` and completed the remaining setup steps manually, without opening SSH. |
| After syncing the frontend to S3, the `/api/v1` routes became unreachable because Nginx stripped the `/api/` prefix while Express mounted the v1 router exactly at `/api/v1`. | Added a dedicated Nginx location block for `/api/v1/` that preserves the full path, separate from the `/api/` location handling legacy routes. |
| The CloudFront URL failed to resolve when re-checked from a different device (noted in the 07/02/2026 review). | Treated this as historical deployment evidence, clearly noting the status so it can be re-verified or accompanied by teardown evidence in a follow-up step, rather than hiding the issue. |

### Lessons Learned:

* Automation scripts (cloud-init/user-data) should not be assumed to always run correctly on every AMI; having an SSM Run Command fallback for manual intervention is essential while still avoiding an open SSH port.
* When a request passes through multiple reverse-proxy layers (CloudFront → Nginx → Express), each layer's path-prefix handling must be checked carefully, since this kind of routing bug is easy to miss until real testing.
* Layered security (IMDSv2, Security Group, OAC, SSM SecureString) is only meaningful if verified directly on the deployed environment via AWS CLI/console — not just by re-reading the CDK code.
* Collecting deployment evidence is just as important as a successful deploy — it should be captured in the moment rather than reconstructed afterward.
* Technical skills (deploying, debugging) need to go hand in hand with awareness of the job market and career positioning — the AWS event reframed CloudBrief not just as an exercise, but as proof of hands-on capability.

### Next Week's Plan:

* Coordinate with teammates to finish the remaining workstreams (frontend dashboard, QA/security regression, news collection pipeline) before the 07/05–07/10/2026 deadline.
* Rerun smoke tests and final end-to-end verification against the deployed environment to prepare for the final demo.
* Run `cdk destroy` after the demo is complete and confirm no EC2, EBS, public IPv4, NAT Gateway, or other billable resource remains — completing the final Definition of Done criterion for Issue #2.
* Consolidate all documentation, evidence, and lessons learned to finalize the internship report.
