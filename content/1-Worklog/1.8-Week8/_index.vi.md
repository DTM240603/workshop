---
title: "Worklog Tuần 8"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 1.8. </b> "
---

**Họ và tên:** Đinh Tuấn Minh &emsp; | &emsp; **MSSV:** 2280601918

**Người hướng dẫn tại đơn vị thực tập:** Nguyễn Gia Hưng – Head of Solution Architect &emsp; | &emsp; **Giảng viên hướng dẫn:** Võ Phạm Thành Luân

**Chủ đề:** Đề xuất Dự án Cuối kỳ, Bài Blog Cộng đồng và Tham dự Event AWS

### Mục tiêu tuần 8:

* Xây dựng đề xuất dự án cuối kỳ tổng hợp kiến thức đã học: hệ thống thu thập và tóm tắt tin tức công nghệ trên kiến trúc Serverless.
* Viết và chia sẻ một bài blog kỹ thuật lên cộng đồng AWS Study Group VN.
* Tham dự sự kiện cộng đồng First Cloud AI Journey để học hỏi kinh nghiệm thực tế và mở rộng mạng lưới quan hệ.
* Chuyển từ giai đoạn học tập từng module riêng lẻ sang giai đoạn ứng dụng tổng hợp kiến thức vào một sản phẩm hoàn chỉnh.

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc                                                                                                                                                                                                                    | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu                            |
| --- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ----------------------------------------- |
| 2   | - Đề xuất dự án cuối kỳ – Hệ thống Thu thập và Tóm tắt Tin tức Công nghệ: tổng quan, động lực và kiến trúc Event-Driven Serverless <br> - Xác định các dịch vụ AWS sử dụng: Lambda (Collector/Processor/Serving), S3, DynamoDB, API Gateway, EventBridge Scheduler | 08/06/2026   | 08/06/2026      | <https://cloudjourney.awsstudygroup.com/> |
| 3   | - Thiết kế luồng xử lý dữ liệu: luồng thu thập (Ingestion), luồng xử lý (Processing với Amazon Bedrock), luồng phục vụ (Serving API) <br> - Lập kế hoạch triển khai 3 giai đoạn: hạ tầng cơ bản (tuần 9), tích hợp AI/API (tuần 10), hoàn thiện/demo (tuần 11) | 09/06/2026   | 09/06/2026      | <https://cloudjourney.awsstudygroup.com/> |
| 4   | - Viết bài blog kỹ thuật chủ đề bảo mật và kiểm toán log trên AWS: xây dựng pipeline CloudTrail → S3 → Glue Crawler → Athena <br> - Đăng bài lên nhóm cộng đồng Facebook AWS Study Group VN kèm ví dụ query thực tế và phần tối ưu chi phí | 10/06/2026   | 10/06/2026      | <https://cloudjourney.awsstudygroup.com/> |
| 5   | - Hoàn thiện và rà soát lại đề xuất dự án cuối kỳ <br> - Chuẩn bị nội dung, câu hỏi và tìm hiểu trước về diễn giả cho sự kiện First Cloud AI Journey Community Day | 11/06/2026   | 11/06/2026      | <https://cloudjourney.awsstudygroup.com/> |
| 6   | - Rà soát phản hồi từ cộng đồng cho bài blog, trả lời bình luận và thảo luận <br> - Chuẩn bị tinh thần và tài liệu tham dự sự kiện Community Day | 12/06/2026   | 12/06/2026      | <https://cloudjourney.awsstudygroup.com/> |
| 7   | - Tham dự sự kiện **First Cloud AI Journey Community Day** tại TP. Hồ Chí Minh: <br>&emsp; + Bài thuyết trình "From First Cloud AI Journey to AWS Partner" <br>&emsp; + Bài thuyết trình "A Scalable URL Shortening Service on AWS" <br>&emsp; + Bài chia sẻ "Câu chuyện thực tế đến văn hóa tại tập đoàn đa quốc gia" <br>&emsp; + Networking với cộng đồng AWS Việt Nam và học viên FCJ đồng khóa | 13/06/2026   | 13/06/2026      | Sự kiện First Cloud AI Journey Community Day |

### Kết quả đạt được tuần 8:

* Hoàn thành đề xuất dự án cuối kỳ "Hệ thống Thu thập và Tóm tắt Tin tức Công nghệ": tổng hợp kiến thức Lambda, S3, API Gateway, DynamoDB, EventBridge vào một kiến trúc serverless hoàn chỉnh, bổ sung Amazon Bedrock cho khả năng tóm tắt bằng AI.
* Viết và đăng thành công bài blog về CloudTrail, Athena và Glue lên cộng đồng AWS Study Group VN, củng cố kiến thức bảo mật của tuần 5 qua việc diễn đạt lại dưới dạng hướng dẫn thực tế.
* Tham dự sự kiện Community Day ngày 13/06/2026, học hỏi từ ba góc nhìn khác nhau: hành trình nghề nghiệp từ sinh viên đến AWS Partner, thiết kế hệ thống thực tế quy mô lớn, và văn hóa làm việc tại doanh nghiệp đa quốc gia.
* Networking trực tiếp với cộng đồng AWS Việt Nam, gặp gỡ học viên FCJ đồng khóa, nhận phản hồi cho ý tưởng dự án cuối kỳ và cập nhật xu hướng ngành.

### Khó khăn và cách khắc phục:

| Khó khăn gặp phải | Cách khắc phục |
| --- | --- |
| Cân bằng giữa tính năng, độ phức tạp và chi phí khi thiết kế đề xuất dự án trong giới hạn ngân sách demo. | Tham khảo AWS Pricing Calculator, ưu tiên các dịch vụ serverless (Lambda, DynamoDB on-demand) để tối ưu chi phí vận hành. |
| Diễn đạt kiến thức kỹ thuật (CloudTrail, Athena) thành bài blog dễ hiểu cho cộng đồng nhiều trình độ khác nhau. | Chia bài viết theo cấu trúc rõ ràng: đặt vấn đề → giải pháp → hướng dẫn từng bước → ví dụ query thực tế → phần chi phí và tối ưu. |
| Lần đầu tham dự sự kiện networking quy mô lớn, còn e ngại khi giao tiếp với người có kinh nghiệm. | Chủ động bắt chuyện với học viên khác, chuẩn bị trước câu hỏi cho diễn giả để tận dụng tối đa thời gian sự kiện. |

### Bài học kinh nghiệm:

* Lộ trình 8 bước từ sinh viên đến AWS Partner (Student Curiosity → Share Back) cho thấy con đường phát triển sự nghiệp cloud có lộ trình rõ ràng, và đóng góp cộng đồng (viết blog, tham dự event) là phần thiết yếu chứ không phải hoạt động phụ.
* Bốn nguyên tắc thiết kế hệ thống rút ra từ dự án URL Shortener (Separation of Concerns, Defense at the Edge, Pre-computation over On-demand, Cache-aside Pattern) là nguồn cảm hứng trực tiếp cho việc thiết kế API serving layer của dự án cuối kỳ.
* Kỹ năng kỹ thuật là điều kiện cần nhưng chưa đủ; khả năng giao tiếp, văn hóa chuyên nghiệp và tư duy business là yếu tố phân biệt kỹ sư giỏi với kỹ sư có giá trị thực sự trong tổ chức.
* Viết và chia sẻ blog mang lại giá trị song hành: vừa củng cố kiến thức qua quá trình diễn đạt, vừa đóng góp cho hệ sinh thái kiến thức cộng đồng và xây dựng reputation cá nhân.

### Kế hoạch tuần tiếp theo:

* Chuyển sang giai đoạn thiết kế chi tiết kiến trúc hạ tầng AWS cho dự án cuối kỳ CloudBrief (Tech News Tracker & Summarizer) – tuần làm việc từ xa (remote).
* Phân tích và vẽ kiến trúc hoàn chỉnh với 13 dịch vụ AWS: EC2, CloudFront, S3, SQS, Bedrock, DynamoDB, EventBridge Scheduler, CloudWatch, SNS, IAM, Backup, Budgets, SSM Parameter Store.
* Thiết kế pipeline dữ liệu ba giai đoạn qua SQS (Collect → Extract → Summarize), cơ chế Dead-Letter Queue và retry contract xử lý lỗi.
* Phân tích chi phí vận hành trong giới hạn $200 AWS demo credit và thiết kế bảo mật theo chiến lược Defense in Depth.
