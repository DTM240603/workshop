---
title: "Worklog Tuần 9"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 1.9. </b> "
---

**Họ và tên:** Đinh Tuấn Minh &emsp; | &emsp; **MSSV:** 2280601918

**Người hướng dẫn tại đơn vị thực tập:** Nguyễn Gia Hưng – Head of Solution Architect &emsp; | &emsp; **Giảng viên hướng dẫn:** Võ Phạm Thành Luân

**Chủ đề:** Thiết kế Kiến trúc Hạ tầng AWS Dự án Cuối kỳ – CloudBrief

### Mục tiêu tuần 9:

* Thiết kế kiến trúc AWS hoàn chỉnh cho dự án cuối kỳ CloudBrief, áp dụng toàn bộ kiến thức đã học từ Tuần 3 đến Tuần 8.
* Phân tích trade-off giữa các lựa chọn kiến trúc (Lambda vs EC2, API Gateway vs EC2 API server, NAT Gateway vs Public Subnet) theo tiêu chí chi phí, vận hành và bảo mật.
* Thiết kế pipeline dữ liệu bất đồng bộ qua Amazon SQS với cơ chế Dead-Letter Queue và retry contract rõ ràng.
* Xây dựng chiến lược bảo mật Defense in Depth và kế hoạch kiểm soát chi phí trong giới hạn $200 AWS demo credit.

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc                                                                                                                                                                                                                    | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu                            |
| --- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ----------------------------------------- |
| 2   | - Giới thiệu dự án CloudBrief (Tech News Tracker & Summarizer): tên, bối cảnh, mục tiêu dự án <br> - Xác định 13 dịch vụ AWS sử dụng: EC2, CloudFront, S3, SQS, Bedrock, DynamoDB, EventBridge Scheduler, CloudWatch, SNS, IAM, Backup, Budgets, SSM Parameter Store | 15/06/2026   | 15/06/2026      | Tài liệu thiết kế nhóm ITSoldier |
| 3   | - Thiết kế Lớp Frontend Delivery: Amazon CloudFront với Origin Access Control (OAC), S3 Frontend Bucket Block Public Access <br> - Thiết kế Lớp EC2 Application: API server, Admin endpoints bảo vệ bằng API key, IMDSv2 bắt buộc, Auto Scaling Group cho Host Recovery | 16/06/2026   | 16/06/2026      | Tài liệu thiết kế nhóm ITSoldier |
| 4   | - Thiết kế Lớp Ingestion & Schedule: nguồn dữ liệu RSS/Hacker News API, lịch thu thập qua systemd timer/EventBridge Scheduler <br> - Thiết kế Managed Data & AI Pipeline: pipeline 3 giai đoạn qua SQS (Collect → Extract → Summarize) với Amazon Bedrock Nova Lite <br> - Thiết kế Dead-Letter Queue và Retry Contract xử lý lỗi (CONTENT_FAILED, SUMMARY_FAILED, SUMMARIZED_PARTIAL) | 17/06/2026   | 17/06/2026      | Tài liệu thiết kế nhóm ITSoldier |
| 5   | - Thiết kế Lớp Monitoring & Security: CloudWatch Logs/Metrics/Alarms, SNS Email Alert Fanout <br> - Thiết kế Lớp Security/Recovery/Cost Controls: IAM Least Privilege, AWS Backup, AWS Budgets (4 mốc cảnh báo $50/$100/$150/$180) <br> - Vẽ luồng xử lý dữ liệu end-to-end: luồng xem dashboard và luồng thu thập/xử lý tin tức | 18/06/2026   | 18/06/2026      | Tài liệu thiết kế nhóm ITSoldier |
| 6   | - Phân tích chi phí vận hành: so sánh cấu hình EC2-first ($20,30/tháng) và cấu hình có ALB ($42,56/tháng) <br> - Phân tích thiết kế bảo mật Defense in Depth (Edge, Network, Application, Identity, Data) và phòng chống XSS <br> - Tổng hợp bài học kinh nghiệm, hoàn thiện bản vẽ kiến trúc và slide giới thiệu dự án CloudBrief <br> - Tổng hợp kiến thức, viết báo cáo tuần 9 | 19/06/2026   | 19/06/2026      | Tài liệu thiết kế nhóm ITSoldier |

### Kết quả đạt được tuần 9:

* Thiết kế kiến trúc AWS thực tế: lần đầu tiên áp dụng toàn bộ kiến thức tích lũy từ Tuần 3–8 vào một bản thiết kế hệ thống hoàn chỉnh với 13 dịch vụ AWS phối hợp, cân bằng giữa tính năng, độ phức tạp và chi phí trong giới hạn $200 budget.
* Phân tích trade-off trong kiến trúc: hiểu sâu hơn về các trade-off thực tế giữa Lambda vs EC2, API Gateway vs EC2 API server, NAT Gateway vs Public Subnet với Security Group.
* Nắm vững pipeline design với SQS: cách dùng SQS để xây dựng pipeline bất đồng bộ có khả năng chịu lỗi cao, với DLQ và retry contract rõ ràng.
* Áp dụng Security Architecture theo Defense in Depth vào hệ thống thực tế: từ CloudFront edge, Security Group network layer, API Key application layer đến IAM Identity layer và Data encryption.
* Rèn luyện tư duy Cost Engineering: mọi quyết định kiến trúc đều bao gồm ước tính chi phí, kỹ năng có giá trị thực tế cao trong môi trường doanh nghiệp.

### Khó khăn và cách khắc phục:

| Khó khăn gặp phải | Cách khắc phục |
| --- | --- |
| Cân bằng giữa tính năng, độ phức tạp và chi phí trong giới hạn $200 AWS demo credit. | Áp dụng tư duy "Cost-First": đánh giá chi phí ngay từ khi lựa chọn dịch vụ thay vì tính toán sau khi thiết kế xong. |
| Thiết kế retry contract và Dead-Letter Queue cho pipeline 3 giai đoạn khá phức tạp khi mới tiếp cận. | Định nghĩa rõ ràng từng loại lỗi (CONTENT_FAILED, SUMMARY_FAILED, SUMMARIZED_PARTIAL) và đường đi retry tương ứng cho mỗi loại. |
| Tuần không có lab thực hành trực tiếp nên khó kiểm chứng thiết kế ngay lập tức. | Đối chiếu với tài liệu AWS Well-Architected Framework và trao đổi với mentor để phản biện và tinh chỉnh thiết kế. |

### Bài học kinh nghiệm:

* Tư duy "Cost-First" trong thiết kế: mọi quyết định về service và cấu hình đều phải được đánh giá về chi phí ngay từ đầu. Việc loại bỏ NAT Gateway, API Gateway và chọn EC2 t4g ARM thay vì x86 giúp kéo dài runway từ ~5 tháng lên ~10 tháng trong cùng $200 budget.
* SQS đóng vai trò như "glue" của kiến trúc pipeline: từng giai đoạn có thể retry độc lập, DLQ cung cấp safety net tự động, visibility timeout tự nhiên ngăn xử lý trùng lặp.
* Fallback Strategy quan trọng cho demo: hệ thống demo phải luôn "hoạt động được" dù có service ngoài đang gặp sự cố – fallback summary đảm bảo pipeline không bị block khi Bedrock lỗi.
* IMDSv2 và không hardcode credentials là bài học trực tiếp từ best practice IAM/KMS/SSM đã học ở Tuần 5, giúp loại bỏ hoàn toàn rủi ro credential leak.

### Kế hoạch tuần tiếp theo:

* Chuyển từ giai đoạn thiết kế sang giai đoạn triển khai thực tế dự án CloudBrief, sử dụng GitHub Issues để phân công công việc nhóm minh bạch.
* Nhận và nắm rõ scope nhiệm vụ được giao: chuẩn bị tài khoản AWS cá nhân, CDK bootstrap/deploy, smoke test và thu thập bằng chứng triển khai.
* Tìm hiểu AWS CDK (Cloud Development Kit) như công cụ Infrastructure as Code để triển khai toàn bộ 13 dịch vụ AWS từ codebase Python/TypeScript.
* Theo dõi tiến độ các thành viên khác trong nhóm: core implementation (CDK/API/security), QA & security checks, frontend dashboard, và pipeline thu thập/tóm tắt tin tức.
