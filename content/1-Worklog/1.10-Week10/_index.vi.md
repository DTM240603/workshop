---
title: "Worklog Tuần 10"
date: 2024-01-01
weight: 2
chapter: false
pre: " <b> 1.10. </b> "
---

**Họ và tên:** Đinh Tuấn Minh &emsp; | &emsp; **MSSV:** 2280601918

**Người hướng dẫn tại đơn vị thực tập:** Nguyễn Gia Hưng – Head of Solution Architect &emsp; | &emsp; **Giảng viên hướng dẫn:** Võ Phạm Thành Luân

**Chủ đề:** Phân công Công việc Nhóm và Bắt đầu Triển khai Dự án CloudBrief

### Mục tiêu tuần 10:

* Áp dụng quy trình làm việc chuyên nghiệp với GitHub Issues để phân công và theo dõi tiến độ dự án nhóm CloudBrief.
* Nắm rõ scope và tiêu chí hoàn thành (Definition of Done) của nhiệm vụ được giao: Deploy CloudBrief to AWS and collect evidence.
* Tìm hiểu AWS CDK (Cloud Development Kit) như công cụ Infrastructure as Code để chuẩn bị triển khai dự án.
* Theo dõi và phối hợp với các thành viên nhóm hoàn thành các hạng mục core implementation, QA, frontend và data pipeline.

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc                                                                                                                                                                                                                    | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu                            |
| --- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ----------------------------------------- |
| 2   | - Tổng quan hoạt động tuần 10: nhóm ITSoldier thống nhất dùng GitHub Issues để phân công (Assignee, Deadline, Scope, "Done when") <br> - Theo dõi Issue #1 "Core CloudBrief implementation: CDK, API, security, integration" được một thành viên hoàn thành và đóng | 22/06/2026   | 22/06/2026      | Repository GitHub nhóm ITSoldier |
| 3   | - Tìm hiểu chi tiết phân công của các thành viên khác: Issue #3 (API QA, Security Checks, Regression Tests), Issue #4 (Read-only CloudBrief Dashboard Frontend), Issue #5 (News Collection, Extraction, and Summarization Pipeline) | 23/06/2026   | 23/06/2026      | Repository GitHub nhóm ITSoldier |
| 4   | - Nhận nhiệm vụ Issue #2 "Deploy CloudBrief to AWS and collect evidence" (deadline 05–10/07/2026) <br> - Xác định scope chi tiết: chuẩn bị tài khoản AWS cá nhân, CDK bootstrap/deploy, deployed smoke tests, evidence capture, cleanup | 24/06/2026   | 24/06/2026      | Tài liệu TEAM_TASK_SPLIT-cloudbrief.md |
| 5   | - Tìm hiểu AWS CDK: khái niệm App và Stack, Constructs 3 cấp độ (L1/L2/L3), CDK Bootstrap <br> - Tìm hiểu lệnh cdk synth, cdk diff, cdk deploy, cdk destroy; so sánh CDK với CloudFormation YAML thuần và Terraform | 25/06/2026   | 25/06/2026      | Tài liệu AWS CDK |
| 6   | - Thực hành đọc và phân tích ví dụ CDK code (S3 bucket + CloudFront với Origin Access Control) <br> - Xác định rõ 5 tiêu chí Definition of Done cho Issue #2 <br> - Tổng hợp kiến thức, viết báo cáo tuần 10 | 26/06/2026   | 26/06/2026      | Tài liệu AWS CDK |

### Kết quả đạt được tuần 10:

* Hoàn thành phân công công việc: toàn bộ 5 nhiệm vụ chính của dự án được phân công rõ ràng với Assignee, Deadline và Scope cụ thể qua GitHub Issues.
* Ghi nhận bước tiến lớn từ đồng đội: Issue #1 (Core implementation: CDK, API, security, integration) đã được đóng – nền tảng codebase quan trọng cho toàn bộ nhóm triển khai và kiểm thử.
* Nắm vững nhiệm vụ deploy (Issue #2): hiểu rõ toàn bộ scope từ chuẩn bị tài khoản AWS, CDK bootstrap/deploy, smoke testing, thu thập evidence đến cleanup sau demo, với Definition of Done rõ ràng gồm 5 tiêu chí đo lường được.
* Học AWS CDK trong thực chiến: lần đầu tiếp cận và áp dụng công cụ Infrastructure as Code quan trọng, kết hợp kỹ năng lập trình với kiến thức AWS.
* Áp dụng quy trình làm việc chuyên nghiệp: GitHub Issues + Definition of Done tương tự môi trường startup và enterprise thực tế.

### Khó khăn và cách khắc phục:

| Khó khăn gặp phải | Cách khắc phục |
| --- | --- |
| Lần đầu tiếp cận AWS CDK, chưa quen cú pháp Python/TypeScript để định nghĩa hạ tầng. | Đọc code mẫu của teammate từ Issue #1, thực hành với ví dụ nhỏ (S3 + CloudFront OAC) trước khi bắt tay vào deploy toàn bộ stack. |
| Xác định rõ ràng phạm vi công việc và tiêu chí hoàn thành cho một nhiệm vụ vận hành/triển khai (khác với code feature) còn khá mới. | Tham khảo tài liệu TEAM_TASK_SPLIT-cloudbrief.md của nhóm và làm rõ Definition of Done với 5 tiêu chí cụ thể, có bằng chứng kèm theo. |
| Deadline chung của dự án khá gấp (05–10/07/2026) trong khi cần chờ Issue #1 hoàn thành mới có thể deploy. | Chủ động tìm hiểu trước AWS CDK và chuẩn bị tài khoản AWS (Budgets, SSM Parameter) song song trong lúc chờ codebase hoàn thiện. |

### Bài học kinh nghiệm:

* Việc Issue #1 được hoàn thành là bước đột phá quan trọng: có một codebase hoàn chỉnh để triển khai giúp giảm thiểu sự phụ thuộc và rủi ro tích hợp ở giai đoạn cuối dự án.
* Definition of Done rõ ràng với tiêu chí đo lường được phản ánh nguyên tắc Agile/Scrum, tránh tình trạng "tưởng xong nhưng chưa xong" thường gặp trong dự án nhóm sinh viên.
* AWS CDK cho phép định nghĩa hạ tầng bằng ngôn ngữ lập trình thực sự, tái sử dụng qua Constructs, ngắn gọn và dễ review hơn nhiều so với viết CloudFormation YAML thuần.
* Quy trình GitHub Issues + Definition of Done + tiêu chí hoàn thành rõ ràng là kinh nghiệm quản lý dự án có giá trị, tương tự môi trường làm việc thực tế tại doanh nghiệp.

### Kế hoạch tuần tiếp theo:

* Bắt đầu thực hiện trực tiếp nhiệm vụ deploy: chuẩn bị tài khoản AWS cá nhân, cấu hình AWS CLI và AWS Budgets.
* Chạy CDK bootstrap, review CDK stack code từ teammate, thực hiện cdk synth/diff và cdk deploy --all để triển khai toàn bộ 12 dịch vụ AWS trong stack.
* Thực hiện các smoke test sau deploy (health check, dashboard, API, admin endpoint protection, security check S3) và thu thập bằng chứng triển khai (evidence) theo yêu cầu AWSFCAJ.
* Phối hợp với các thành viên khác đang hoàn thiện frontend dashboard, pipeline xử lý dữ liệu và bộ QA/security check, hướng đến demo hoàn chỉnh trước ngày 10/07/2026.
