---
title: "Week 12 Worklog"
date: 2024-01-01
weight: 2
chapter: false
pre: " <b> 1.12. </b> "
---

**Full Name:** Dinh Tuan Minh &emsp; | &emsp; **Student ID:** 2280601918

**Company Mentor:** Nguyen Gia Hung – Head of Solution Architect &emsp; | &emsp; **Academic Supervisor:** Vo Pham Thanh Luan

**Topic:** Finalizing the CloudBrief Project and Internship Wrap-Up (Final Week)

### Week 12 Objectives:

* Track and confirm that all 5 GitHub Issues of the CloudBrief project (ITSoldier team) have been completed and closed.
* Re-verify the CloudBrief system on the latest environment after a teammate's stabilized redeploy, checking it against Issue #2's Definition of Done.
* Review the resource cleanup procedure and document why cleanup must remain pending while the shared production demo is still active.
* Finalize the entire internship report using Hugo and submit it to the internship company, wrapping up 12 weeks in the First Cloud AI Journey program.

### Tasks to be carried out this week:
| Day | Task                                                                                                                                                                                                                    | Start Date | Completion Date | Reference Material                        |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ---------- | --------------- | ----------------------------------------- |
| 2   | - Tracked and reviewed the team's final Pull Requests: the frontend dashboard (Issue #4), QA/security regression (Issue #3), backend pipeline readiness, and Issue #1's stabilized redeploy (fixing the DynamoDB batch write, CSP, run ordering, and runtime packaging bugs) <br> - Confirmed all 5 project Issues were in Closed status | 07/06/2026 | 07/06/2026      | GitHub Issues – ITSoldier |
| 3   | - Reran a personal smoke test against the new CloudFront URL after the redeploy (`https://d3u5pkyxnd3uus.cloudfront.net`), checking it against every item in Issue #2's Definition of Done <br> - Confirmed the dashboard displayed correctly: 5/5 articles `SUMMARIZED`, current run `COMPLETED`, no console errors | 07/07/2026 | 07/07/2026      | Issue #2 – Deploy CloudBrief to AWS |
| 4   | - Consolidated all collected deployment evidence (screenshots of CDK deploy, CloudFront, EC2, DynamoDB, S3, CloudWatch, SNS, Budget, dashboard) <br> - Wrote and finalized the Workshop report content in Hugo based on all evidence collected | 07/08/2026 | 07/08/2026      | ITSoldier team deployment evidence |
| 5   | - Reviewed the cleanup runbook for the `cloudbrief-dev` stack and listed the resources that must be checked before destroy (CloudFront, EC2/ASG, DynamoDB, S3, CloudWatch, SNS, Backup, Budgets) <br> - Recorded that cleanup remained pending because the shared production demo was still active and the image-processing DLQ still needed follow-up before destructive actions could be approved | 07/09/2026 | 07/09/2026      | Cleanup runbook and deployment audit |
| 6   | - Finalized the entire internship report using Hugo: Worklog, Proposal, Blogs, Events, Workshop, Self-Evaluation, and Feedback <br> - Submitted the report to the internship company, wrapping up the 12-week internship, concluding the term at First Cloud AI Journey | 07/10/2026 | 07/10/2026      | Final internship report |

### Week 12 Achievements:

* All 5 GitHub Issues of the CloudBrief project (core implementation, deploy, QA/security, frontend, data pipeline) were completed and closed on schedule.
* Successfully verified that the system ran stably on the final redeploy: the dashboard displayed real data correctly, the Collect → Extract → Summarize pipeline ran accurately, with no console errors or asset-loading failures.
* Finalized the CloudBrief project with its full architecture, deployment process, and security controls documented in detail in the Hugo report.
* Documented the cleanup and recovery procedure in the Workshop report, including the operational reason why `cdk destroy` could not yet be executed on the shared production demo environment.
* Fully finalized the 12-week internship report using Hugo and submitted it to the internship company, concluding the internship exactly on 07/10/2026.

### Challenges and Solutions:

| Challenge | Solution |
| --- | --- |
| A teammate had redeployed the system with a different CloudFront URL and EC2 instance ID than the original deployment in Issue #2, creating potential confusion when reconciling evidence. | Clearly documented both deployments (the original and the stabilized redeploy) in the report, noting the origin of each change before considering the Definition of Done met. |
| Time pressure from having to complete final technical verification, finalize the Hugo report, and prepare it for submission all within the same week. | Split the work into clear, independent daily tracks (technical verification → report writing → cleanup planning → finalizing & submitting the report) instead of cramming everything into the last day. |

### Lessons Learned:

* A team project isn't truly "done" once Pull Requests are merged — a final re-verification pass on the environment that will be documented in the report is essential, since the system may have changed after other teammates' updates.
* Teardown (`cdk destroy`) should only be executed after the shared environment is no longer needed and all operational follow-ups are closed; otherwise the correct action is to document the pending cleanup state explicitly.
* Assigning clear task ownership via GitHub Issues from the start (Week 10) made the final sprint far more organized, with each member knowing exactly their scope and completion criteria.
* Writing the report alongside the actual work, rather than deferring it to the end, preserves far greater accuracy than reconstructing events after the project has already closed.
* Technical skill (design, deployment, verification) needs to be paired with the ability to present and synthesize it into a coherent report — this is what makes the CloudBrief project stand out in a personal portfolio going forward.

### Internship Summary:

After 12 weeks in the First Cloud AI Journey program (04/17/2026 – 07/10/2026), I progressed from learning basic AWS concepts (Week 1) to personally designing, deploying, and operating a complete cloud system — the **CloudBrief** project — on a real AWS account, following the architecture, security, and cost standards learned throughout the program. This forms an important foundation for my Cloud Engineer career path after graduation.
