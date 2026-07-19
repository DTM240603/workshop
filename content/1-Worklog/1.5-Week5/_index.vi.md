---
title: "Worklog Tuần 5"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 1.5. </b> "
---

**Họ và tên:** Đinh Tuấn Minh &emsp; | &emsp; **MSSV:** 2280601918

**Người hướng dẫn tại đơn vị thực tập:** Nguyễn Gia Hưng – Head of Solution Architect &emsp; | &emsp; **Giảng viên hướng dẫn:** Võ Phạm Thành Luân

**Chủ đề:** Bảo mật và Quản lý Danh tính trên AWS

### Mục tiêu tuần 5:

* Hiểu Mô hình Trách nhiệm Chia sẻ (Shared Responsibility Model) giữa AWS và khách hàng.
* Nắm vững AWS IAM: User, Group, Role, Policy và các kỹ thuật nâng cao như Tag-Based Access Control, Permission Boundary, IAM Condition.
* Phân biệt Amazon Cognito với IAM; hiểu AWS Organization, Service Control Policy và AWS Identity Center cho quản trị multi-account.
* Thực hành Amazon KMS để mã hóa dữ liệu và AWS Security Hub để giám sát bảo mật tập trung qua các lab thực hành.

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc                                                                                                                                                                                                                    | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu                            |
| --- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ----------------------------------------- |
| 2   | - Mô hình Trách nhiệm Chia sẻ: "Security OF the Cloud" (AWS) và "Security IN the Cloud" (khách hàng) <br> - AWS IAM: User, Group, Role, Policy; đánh giá policy (implicit deny → explicit allow → explicit deny) <br> - Best Practice IAM: MFA, Least Privilege, IAM Role thay vì Access Key, IAM Access Analyzer | 18/05/2026   | 18/05/2026      | <https://cloudjourney.awsstudygroup.com/> |
| 3   | - Amazon Cognito: User Pools (authentication) và Identity Pools (federated identities) <br> - AWS Organization: Management Account, Organizational Unit, Member Account, Service Control Policy (SCP) <br> - AWS Identity Center (SSO): Permission Set, tích hợp Active Directory/Okta/Azure AD | 19/05/2026   | 19/05/2026      | <https://cloudjourney.awsstudygroup.com/> |
| 4   | - Amazon KMS: AWS Managed Key, Customer Managed Key, AWS Owned Key; Envelope Encryption, Key Policy, Automatic Key Rotation <br> - AWS Security Hub: tổng hợp findings, Security Score, các chuẩn compliance <br> - **Thực hành (Lab: Security Hub):** kích hoạt, đánh giá Security Score, phân tích failed control <br> - **Thực hành (Lab: Quản lý Tag và Resource Group):** gán/sửa/lọc tag, tạo Resource Group | 20/05/2026   | 20/05/2026      | <https://cloudjourney.awsstudygroup.com/> |
| 5   | - **Thực hành (Lab: Tự động hóa EC2 với Lambda và Slack Webhook):** tạo VPC/SG/EC2, IAM Role cho Lambda, Lambda start/stop theo lịch EventBridge, thông báo qua Slack <br> - **Thực hành (Lab: IAM nâng cao – Switch Role và Tag-Based Access Control):** IAM Policy theo Condition ResourceTag, Switch Role, kiểm tra AccessDenied <br> - **Thực hành (Lab: IAM giới hạn quyền hạn):** Restriction Policy, test hành động được phép/bị từ chối <br> - **Thực hành (Lab: IAM Switch Role giới hạn theo IP và thời gian):** Condition aws:SourceIp và aws:CurrentTime | 21/05/2026   | 21/05/2026      | <https://cloudjourney.awsstudygroup.com/> |
| 6   | - **Thực hành (Lab: KMS, CloudTrail và Amazon Athena):** tạo Customer Managed Key, mã hóa S3 (SSE-KMS), bật CloudTrail, dùng Athena query log bằng SQL <br> - **Thực hành (Lab: IAM Access Key và IAM Role):** so sánh long-term credentials và temporary credentials khi EC2 truy cập S3 <br> - Tổng hợp kiến thức, viết báo cáo tuần 5 | 22/05/2026   | 22/05/2026      | <https://cloudjourney.awsstudygroup.com/> |

### Kết quả đạt được tuần 5:

* Nắm vững mô hình Shared Responsibility – nền tảng tư duy bảo mật cloud, xác định rõ ranh giới trách nhiệm AWS và khách hàng.
* Hiểu sâu AWS IAM: User, Group, Role, Policy và các kỹ thuật nâng cao như TBAC, Permission Boundary, IAM Condition, Switch Role.
* Phân biệt Amazon Cognito (identity cho end-user ứng dụng) với IAM (identity cho AWS resources) – hai dịch vụ hay bị nhầm lẫn.
* Nắm được AWS Organization và SCP như giải pháp quản trị quyền hạn ở cấp account, nền tảng của kiến trúc multi-account enterprise.
* Hiểu AWS Identity Center là giải pháp SSO tập trung cho môi trường có nhiều AWS account và ứng dụng SaaS.
* Nắm vững Amazon KMS: phân biệt AWS Managed Key và Customer Managed Key, hiểu cơ chế Key Policy và Envelope Encryption.
* Thực hành AWS Security Hub như "glass pane" tổng hợp findings bảo mật và đo lường compliance theo framework chuẩn.
* Thực hành 8 lab toàn diện: từ giám sát bảo mật, mã hóa dữ liệu, audit logging, đến tự động hóa có bảo mật và quản lý credentials đúng cách.

### Khó khăn và cách khắc phục:

| Khó khăn gặp phải | Cách khắc phục |
| --- | --- |
| Dễ nhầm lẫn giữa Identity-based Policy, Resource-based Policy, Permission Boundary và Service Control Policy (SCP). | Lập bảng so sánh phạm vi áp dụng: gán vào identity hay resource, áp dụng ở cấp account hay Organization. |
| Nhiều loại KMS Key (AWS Managed, Customer Managed, AWS Owned) dễ nhầm lẫn về quyền quản lý và chi phí. | Ghi chú đặc điểm, khả năng rotate và chi phí của từng loại key để chọn đúng loại cho từng nhu cầu. |
| Logic đánh giá IAM Policy (explicit deny/allow/implicit deny) khá phức tạp khi kiểm thử nhiều lab liên tiếp. | Dùng IAM Policy Simulator để kiểm tra policy trước khi triển khai thực tế. |

### Bài học kinh nghiệm:

* Ngay cả một tài khoản AWS mới tạo cũng đã có nhiều Security Hub findings do thiếu cấu hình MFA, CloudTrail hoặc các setting bảo mật cơ bản.
* Pattern Lambda + EventBridge Scheduler là giải pháp cost optimization phổ biến, có thể tiết kiệm đáng kể chi phí EC2 bằng cách tắt instance ngoài giờ làm việc.
* Tagging là kỷ luật quản trị cloud quan trọng: không chỉ giúp tổ chức tài nguyên mà còn là cơ sở cho IAM Policy có điều kiện, Cost Allocation Reports và tự động hóa.
* Tag-Based Access Control (TBAC) là nền tảng cho chiến lược IAM ở môi trường enterprise nơi việc quản lý policy thủ công cho từng resource là bất khả thi.
* Explicit Deny luôn thắng bất kỳ Allow nào, trong khi thiếu Allow đồng nghĩa với từ chối ngầm (Implicit Deny) – kỹ năng viết và test IAM policy chính xác là yêu cầu thiết yếu.
* KMS (mã hóa dữ liệu), CloudTrail (audit logging) và Athena (phân tích log) tạo thành trụ cột của chiến lược Data Security và Security Monitoring trên AWS.
* IAM Condition (giới hạn theo IP, theo thời gian) là kỹ thuật Zero Trust thực tế, ngăn chặn việc lạm dụng credentials bị đánh cắp ngoài môi trường kiểm soát.
* IAM Role sử dụng temporary credentials tự động rotate, luôn được khuyến nghị hơn Access Key (long-term credentials) cho EC2, Lambda và mọi compute service.

### Kế hoạch tuần tiếp theo:

* Chuyển sang chủ đề Dịch vụ Cơ sở dữ liệu trên AWS: ôn tập các khái niệm nền tảng (SQL vs NoSQL, ACID vs BASE, OLTP vs OLAP).
* Tìm hiểu Amazon RDS (kiến trúc, Multi-AZ, Read Replica, backup/PITR) và Amazon Aurora (kiến trúc storage phân tán, Aurora Cluster, Serverless v2, Global Database).
* Tìm hiểu Amazon Redshift (data warehouse, MPP, Redshift Spectrum) và Amazon ElastiCache (Redis, Memcached, caching patterns).
* Thực hành triển khai kiến trúc 3-tier với RDS trong private subnet, và thực hành toàn bộ quy trình di chuyển database với AWS Database Migration Service (DMS) kết hợp Schema Conversion Tool (SCT).
