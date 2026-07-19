---
title: "Worklog Tuần 12"
date: 2024-01-01
weight: 2
chapter: false
pre: " <b> 1.12. </b> "
---

**Họ và tên:** Đinh Tuấn Minh &emsp; | &emsp; **MSSV:** 2280601918

**Người hướng dẫn tại đơn vị thực tập:** Nguyễn Gia Hưng – Head of Solution Architect &emsp; | &emsp; **Giảng viên hướng dẫn:** Võ Phạm Thành Luân

**Chủ đề:** Hoàn tất dự án CloudBrief và Tổng kết thực tập (Tuần cuối)

### Mục tiêu tuần 12:

* Theo dõi và xác nhận toàn bộ 5 GitHub Issue của dự án CloudBrief (nhóm ITSoldier) đã được hoàn thành và đóng.
* Tự xác minh lại (re-verify) hệ thống CloudBrief trên môi trường mới nhất sau bản redeploy ổn định của đồng đội, đối chiếu với Definition of Done của Issue #2.
* Rà soát quy trình cleanup và ghi nhận rõ lý do vì sao chưa thể chạy `cdk destroy` khi production demo dùng chung vẫn còn hoạt động.
* Hoàn thiện toàn bộ báo cáo thực tập bằng Hugo và nộp lại cho đơn vị thực tập, tổng kết 12 tuần thực tập tại chương trình First Cloud AI Journey.

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc                                                                                                                                                                                                                    | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu                            |
| --- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ----------------------------------------- |
| 2   | - Theo dõi và tổng hợp các Pull Request cuối cùng của nhóm: frontend dashboard (Issue #4), QA/security regression (Issue #3), backend pipeline readiness và bản redeploy ổn định hóa của Issue #1 (sửa lỗi DynamoDB batch write, CSP, thứ tự run, đóng gói runtime) <br> - Xác nhận cả 5 Issue của dự án đã ở trạng thái Closed | 06/07/2026   | 06/07/2026      | GitHub Issues – ITSoldier |
| 3   | - Tự chạy lại smoke test cá nhân trên CloudFront URL mới sau bản redeploy (`https://d3u5pkyxnd3uus.cloudfront.net`), đối chiếu từng mục trong Definition of Done của Issue #2 <br> - Xác nhận dashboard hiển thị đúng: 5/5 bài viết `SUMMARIZED`, current run `COMPLETED`, không còn lỗi console | 07/07/2026   | 07/07/2026      | Issue #2 – Deploy CloudBrief to AWS |
| 4   | - Tổng hợp toàn bộ bằng chứng triển khai đã thu thập (ảnh chụp CDK deploy, CloudFront, EC2, DynamoDB, S3, CloudWatch, SNS, Budget, dashboard) <br> - Viết và hoàn thiện nội dung báo cáo Workshop bằng Hugo dựa trên toàn bộ bằng chứng đã thu thập | 08/07/2026   | 08/07/2026      | Bằng chứng triển khai nhóm ITSoldier |
| 5   | - Rà soát runbook cleanup của stack `cloudbrief-dev` và liệt kê các tài nguyên cần kiểm tra trước khi destroy (CloudFront, EC2/ASG, DynamoDB, S3, CloudWatch, SNS, Backup, Budgets) <br> - Ghi nhận cleanup vẫn ở trạng thái pending vì production demo dùng chung còn hoạt động và image-processing DLQ vẫn cần được xử lý trước khi phê duyệt hành động destructive | 09/07/2026   | 09/07/2026      | Runbook cleanup và deployment audit |
| 6   | - Hoàn thiện toàn bộ báo cáo thực tập bằng Hugo: Worklog, Proposal, Blogs, Events, Workshop, Tự đánh giá và Feedback <br> - Nộp báo cáo cho đơn vị thực tập, tổng kết quá trình 12 tuần, kết thúc kỳ thực tập tại First Cloud AI Journey | 10/07/2026   | 10/07/2026      | Báo cáo thực tập cuối kỳ |

### Kết quả đạt được tuần 12:

* Toàn bộ 5 GitHub Issue của dự án CloudBrief (core implementation, deploy, QA/security, frontend, data pipeline) đã được hoàn thành và đóng đúng hạn.
* Xác minh thành công hệ thống hoạt động ổn định trên bản redeploy cuối cùng: dashboard hiển thị đúng dữ liệu thật, pipeline Collect → Extract → Summarize chạy chính xác, không còn lỗi console hay lỗi tải asset.
* Hoàn thiện dự án CloudBrief với đầy đủ kiến trúc, quy trình triển khai và các control bảo mật được ghi lại chi tiết trong báo cáo Hugo.
* Hoàn thiện phần tài liệu cleanup và recovery trong Workshop, đồng thời ghi rõ lý do vận hành khiến `cdk destroy` chưa thể được thực thi trên production demo dùng chung.
* Hoàn thiện đầy đủ báo cáo thực tập 12 tuần bằng Hugo và nộp lại cho đơn vị thực tập, kết thúc kỳ thực tập đúng ngày 10/07/2026.

### Khó khăn và cách khắc phục:

| Khó khăn gặp phải | Cách khắc phục |
| --- | --- |
| Hệ thống đã được đồng đội redeploy lại với CloudFront URL và EC2 instance ID khác so với lần deploy đầu tiên trong Issue #2, dễ gây nhầm lẫn khi đối chiếu bằng chứng. | Tổng hợp rõ ràng cả hai bản deploy (ban đầu và sau ổn định hóa) trong tài liệu, ghi chú rõ nguồn gốc từng thay đổi trước khi công nhận Definition of Done. |
| Áp lực thời gian khi vừa phải xác minh kỹ thuật lần cuối, vừa hoàn thiện nội dung báo cáo Hugo, vừa chuẩn bị nộp báo cáo trong cùng một tuần. | Tách rõ thành các luồng công việc độc lập theo từng ngày (xác minh kỹ thuật → viết báo cáo → rà soát kế hoạch cleanup → hoàn thiện & nộp báo cáo) thay vì làm dồn vào cuối tuần. |

### Bài học kinh nghiệm:

* Một dự án nhóm chưa thực sự "xong" khi các Pull Request được merge — cần một vòng xác minh cuối (re-verification) trên đúng môi trường sẽ được ghi nhận trong báo cáo, vì hệ thống có thể đã thay đổi do thành viên khác cập nhật sau đó.
* Teardown (`cdk destroy`) chỉ nên được thực hiện khi môi trường dùng chung không còn phục vụ demo và các đầu việc vận hành đã được đóng; nếu chưa, cần ghi rõ trạng thái cleanup pending trong tài liệu.
* Việc phân công công việc rõ ràng qua GitHub Issues ngay từ đầu (Tuần 10) giúp giai đoạn nước rút cuối kỳ diễn ra có tổ chức, mỗi thành viên biết chính xác phần việc và tiêu chí hoàn thành của mình.
* Viết báo cáo song song với quá trình làm việc, thay vì dồn lại vào cuối kỳ, giúp giữ được độ chính xác cao hơn nhiều so với việc hồi tưởng sau khi dự án đã khép lại.
* Kỹ năng kỹ thuật (thiết kế, triển khai, xác minh) cần đi cùng khả năng trình bày và tổng hợp thành một báo cáo mạch lạc — đây chính là điều tạo nên sự khác biệt khi đưa dự án CloudBrief vào portfolio cá nhân sau này.

### Tổng kết kỳ thực tập:

Sau 12 tuần thực tập tại chương trình First Cloud AI Journey (17/04/2026 – 10/07/2026), em đã đi từ việc làm quen với các khái niệm AWS cơ bản (Tuần 1) đến việc tự tay thiết kế, triển khai và vận hành một hệ thống cloud hoàn chỉnh — dự án **CloudBrief** — trên tài khoản AWS thật, đúng theo các tiêu chuẩn về kiến trúc, bảo mật và chi phí đã học trong suốt chương trình. Đây là nền tảng quan trọng cho định hướng nghề nghiệp Cloud Engineer của em sau khi tốt nghiệp.
