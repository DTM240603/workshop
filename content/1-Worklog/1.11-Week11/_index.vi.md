---
title: "Worklog Tuần 11"
date: 2024-01-01
weight: 2
chapter: false
pre: " <b> 1.11. </b> "
---

**Họ và tên:** Đinh Tuấn Minh &emsp; | &emsp; **MSSV:** 2280601918

**Người hướng dẫn tại đơn vị thực tập:** Nguyễn Gia Hưng – Head of Solution Architect &emsp; | &emsp; **Giảng viên hướng dẫn:** Võ Phạm Thành Luân

**Chủ đề:** Deploy CloudBrief lên AWS và thu thập bằng chứng triển khai (GitHub Issue #2)

### Mục tiêu tuần 11:

* Thực hiện đúng phạm vi công việc của Issue #2 "Deploy CloudBrief to AWS and collect evidence": chuẩn bị tài khoản AWS, CDK bootstrap/deploy, cấu hình EC2, kiểm thử trên môi trường đã triển khai và thu thập bằng chứng.
* Xác minh hệ thống CloudBrief hoạt động đúng trên tài khoản AWS thật (không chỉ trên mã nguồn/CDK output cục bộ).
* Kiểm tra các control bảo mật đã thiết kế (IMDSv2, Security Group giới hạn theo CloudFront, S3 Block Public Access, API key chỉ lưu hash trong SSM) thực sự có hiệu lực trên môi trường deploy.
* Thu thập đầy đủ bằng chứng triển khai theo yêu cầu AWSFCAJ để phục vụ báo cáo cuối kỳ.

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc                                                                                                                                                                                                                    | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu                            |
| --- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ----------------------------------------- |
| 2   | - Đọc kỹ Issue #2 (scope, security checklist, Definition of Done) và tài liệu `TEAM_TASK_SPLIT-cloudbrief.md`/`CLOUDBRIEF_EC2_AGENT_SPEC.md` <br> - Chuẩn bị tài khoản AWS: tạo IAM user riêng cho deploy, cấu hình AWS CLI cho `us-east-1`, kiểm tra quyền truy cập Bedrock `amazon.nova-lite-v1:0`, chuẩn bị `DEMO_API_KEY` và `BUDGET_EMAIL` | 29/06/2026   | 29/06/2026      | TEAM_TASK_SPLIT-cloudbrief.md |
| 3   | - Chạy `bun install`, `bun run build`, `bun run test`, `bun run cdk synth` cục bộ để xác nhận không có lỗi trước khi deploy <br> - Review lại CDK stack code của teammate (Issue #1: core implementation) để hiểu rõ tài nguyên sẽ được tạo | 30/06/2026   | 30/06/2026      | CLOUDBRIEF_EC2_AGENT_SPEC.md |
| 4   | - Xác thực AWS CLI (`aws sts get-caller-identity`), chạy `cdk bootstrap` và `cdk deploy --require-approval never` <br> - Cấu hình EC2 qua AWS SSM Run Command: xử lý xung đột gói `curl-minimal` trên Amazon Linux 2023, cài Bun runtime, tạo file biến môi trường, cài Nginx reverse proxy, build & upload app bundle, kích hoạt systemd service <br> - Chạy smoke test đầu tiên (`/health`, `/articles`, `/collect` có/không API key) | 01/07/2026   | 01/07/2026      | docs/operations.md |
| 5   | - Phát hiện và xử lý lỗi định tuyến Nginx cho `/api/v1` (Nginx cắt tiền tố `/api/` trong khi Express mount v1 router tại `/api/v1`) <br> - Kiểm thử pipeline end-to-end: kích hoạt `/collect`, xác nhận bài viết đi qua đủ 3 trạng thái Collect → Extract → Summarize và hiển thị qua CloudFront <br> - Thu thập bằng chứng triển khai: ảnh chụp CDK deploy, CloudFront, EC2, DynamoDB, S3, CloudWatch Logs/Alarms, SNS, AWS Budget | 02/07/2026   | 02/07/2026      | docs/operations.md |
| 6   | - Rà soát checklist bảo mật theo Issue #2: xác nhận IMDSv2 bắt buộc, Security Group EC2 chỉ nhận traffic từ CloudFront, hai S3 bucket bật Block Public Access, API key chỉ lưu bản băm SHA-256 trong SSM SecureString, EC2 Instance Role không có quyền admin <br> - Tổng hợp toàn bộ bằng chứng theo 5 tiêu chí Definition of Done, viết báo cáo triển khai | 03/07/2026   | 03/07/2026      | Issue #2 – Deploy CloudBrief to AWS |
| 7   | - Tham dự sự kiện **"Amazon Web Services (AWS): Enterprise Cloud Architectures and Industry Applications – Featuring Cloud Kinetics & Renova Cloud"** tại AWS Office, tòa nhà Bitexco: 4 bài chia sẻ về thị trường tuyển dụng Cloud/Data, kinh nghiệm Data Engineer thực tế, kỹ năng mềm và tư duy dùng AI cho Fresher <br> - Networking với cộng đồng AWS Việt Nam | 04/07/2026   | 04/07/2026      | Sự kiện AWS Enterprise Cloud Architectures |

### Kết quả đạt được tuần 11:

* Triển khai thành công toàn bộ hạ tầng CloudBrief lên tài khoản AWS thật bằng `cdk deploy`, không có resource nào ở trạng thái ROLLBACK/FAILED.
* Cấu hình EC2 hoạt động ổn định với API server và worker process chạy qua systemd, vượt qua sự cố cloud-init ban đầu bằng cách xử lý thủ công qua SSM Run Command.
* Xác nhận dashboard và API đều truy cập được qua CloudFront HTTPS; smoke test và kiểm thử pipeline end-to-end đều pass (Collect → Extract → Summarize → hiển thị trên dashboard).
* Xác minh các control bảo mật thiết kế từ Tuần 9 đều có hiệu lực thực tế trên môi trường deploy (IMDSv2, Security Group giới hạn CloudFront, S3 Block Public Access, API key hash trong SSM).
* Thu thập đầy đủ bằng chứng triển khai (ảnh chụp CloudFormation, CloudFront, EC2, DynamoDB, S3, CloudWatch, SNS, Budget) đáp ứng 4/5 tiêu chí Definition of Done của Issue #2.
* Tham dự sự kiện AWS về kiến trúc doanh nghiệp và thị trường tuyển dụng, có thêm góc nhìn thực tế để định vị dự án CloudBrief khi phỏng vấn sau này.

### Khó khăn và cách khắc phục:

| Khó khăn gặp phải | Cách khắc phục |
| --- | --- |
| Script cloud-init tự động thất bại do xung đột gói `curl-minimal` có sẵn trên Amazon Linux 2023, khiến EC2 không tự cài đặt được ứng dụng. | Dùng AWS Systems Manager (SSM) Run Command để chạy `dnf install -y --allowerasing curl unzip amazon-cloudwatch-agent` và hoàn tất các bước cấu hình còn lại thủ công, không cần mở SSH. |
| Sau khi đồng bộ frontend lên S3, các route `/api/v1` không truy cập được vì Nginx cắt tiền tố `/api/` trong khi Express mount router v1 tại đúng `/api/v1`. | Thêm một location block Nginx riêng cho `/api/v1/` giữ nguyên đường dẫn, tách biệt với location `/api/` xử lý các route cũ. |
| CloudFront URL không resolve được khi kiểm tra lại từ thiết bị khác (ghi nhận trong review 02/07/2026). | Xem đây là bằng chứng triển khai mang tính lịch sử, ghi chú rõ trạng thái để bổ sung xác minh hoặc bằng chứng teardown ở bước tiếp theo thay vì che giấu vấn đề. |

### Bài học kinh nghiệm:

* Không nên giả định script tự động hóa (cloud-init/user-data) luôn chạy đúng trên mọi AMI; cần có phương án dự phòng bằng SSM Run Command để can thiệp thủ công mà vẫn tuân thủ nguyên tắc không mở port SSH ra ngoài.
* Khi một request đi qua nhiều lớp reverse proxy (CloudFront → Nginx → Express), cần kiểm tra kỹ cách từng lớp xử lý path prefix, vì lỗi định tuyến kiểu này rất dễ bị bỏ sót cho đến khi kiểm thử thực tế.
* Bảo mật nhiều lớp (IMDSv2, Security Group, OAC, SSM SecureString) chỉ có giá trị nếu được xác minh trực tiếp trên môi trường đã deploy bằng AWS CLI/console, không nên chỉ tin vào việc đọc lại CDK code.
* Thu thập bằng chứng triển khai (evidence) là một phần công việc quan trọng không kém việc deploy thành công — cần ghi lại ngay trong lúc thao tác thay vì làm lại sau.
* Kỹ năng kỹ thuật (deploy, debug) cần đi cùng nhận thức về thị trường tuyển dụng và định vị nghề nghiệp — bài học từ sự kiện AWS giúp nhìn dự án CloudBrief không chỉ như một bài tập mà như một minh chứng năng lực thực chiến.

### Kế hoạch tuần tiếp theo:

* Phối hợp với các thành viên nhóm hoàn thiện các phần còn lại (frontend dashboard, QA/security regression, pipeline thu thập tin) trước hạn chót (05–10/07/2026).
* Chạy lại smoke test và kiểm thử end-to-end lần cuối trên môi trường deploy để chuẩn bị cho buổi demo cuối kỳ.
* Thực hiện `cdk destroy` sau khi demo hoàn tất và xác minh không còn EC2, EBS, public IPv4, NAT Gateway hay tài nguyên nào khác phát sinh chi phí — hoàn tất tiêu chí Definition of Done cuối cùng của Issue #2.
* Tổng hợp toàn bộ tài liệu, bằng chứng và bài học kinh nghiệm để hoàn thiện báo cáo thực tập cuối kỳ.
