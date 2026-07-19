---
title: "Worklog Tuần 4"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 1.4. </b> "
---

**Họ và tên:** Đinh Tuấn Minh &emsp; | &emsp; **MSSV:** 2280601918

**Người hướng dẫn tại đơn vị thực tập:** Nguyễn Gia Hưng – Head of Solution Architect &emsp; | &emsp; **Giảng viên hướng dẫn:** Võ Phạm Thành Luân

**Chủ đề:** Dịch vụ Lưu trữ trên AWS

### Mục tiêu tuần 4:

* Hiểu tổng quan hệ sinh thái dịch vụ lưu trữ AWS: Block Storage, File Storage, Object Storage và các giải pháp hybrid/migration.
* Nắm vững Amazon S3 nâng cao: Access Point, các Storage Class, Lifecycle Policy, Static Website Hosting, CORS và các lớp kiểm soát truy cập.
* Hiểu vai trò của AWS Snow Family, AWS Storage Gateway và AWS Backup trong các kịch bản migration và hybrid cloud.
* Thực hành nhiều lab liên quan đến backup, migration máy ảo, hybrid storage và phân phối nội dung tĩnh theo chuẩn AWS.

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc                                                                                                                                                                                                                    | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu                            |
| --- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ----------------------------------------- |
| 2   | - Tổng quan dịch vụ lưu trữ trên AWS: Block Storage, File Storage, Object Storage <br> - Amazon S3: tổng quan, Access Point và các Storage Class (Standard, Intelligent-Tiering, Standard-IA, One Zone-IA, Glacier...) và S3 Lifecycle Policy | 11/05/2026   | 11/05/2026      | <https://cloudjourney.awsstudygroup.com/> |
| 3   | - S3 Static Website Hosting và CORS <br> - Các lớp kiểm soát truy cập S3: Bucket Policy, IAM Policy, ACL, Block Public Access, Pre-signed URL <br> - Object Key, Prefix và Performance; Multipart Upload; S3 Transfer Acceleration <br> - Amazon S3 Glacier: Instant/Flexible Retrieval, Deep Archive, Vault Lock | 12/05/2026   | 12/05/2026      | <https://cloudjourney.awsstudygroup.com/> |
| 4   | - AWS Snow Family (Snowcone, Snowball Edge, Snowmobile), AWS Storage Gateway, AWS Backup <br> - **Thực hành (Lab: AWS Backup – Sao lưu và khôi phục):** <br>&emsp; + Tạo Backup Plan với retention 7 ngày, gán tài nguyên theo tag <br>&emsp; + Cấu hình SNS notification khi backup job hoàn thành/thất bại <br>&emsp; + Test restore từ recovery point <br> - **Thực hành (Lab: VM Import/Export):** <br>&emsp; + Export máy ảo VMware thành OVA/VMDK, upload lên S3 <br>&emsp; + Import thành AMI và deploy EC2 instance từ AMI | 13/05/2026   | 13/05/2026      | <https://cloudjourney.awsstudygroup.com/> |
| 5   | - **Thực hành (Lab: AWS Storage Gateway):** <br>&emsp; + Triển khai Storage Gateway (File Gateway) trên EC2, kích hoạt qua Console <br>&emsp; + Tạo NFS/SMB File Share liên kết với S3 bucket, mount trên máy on-premises <br> - **Thực hành (Lab: Amazon FSx for Windows File Server):** <br>&emsp; + Tạo FSx Multi-AZ (SSD và HDD), tạo file share và test performance <br>&emsp; + Bật Data Deduplication, Shadow Copies, User Storage Quotas; scale throughput/storage không downtime | 14/05/2026   | 14/05/2026      | <https://cloudjourney.awsstudygroup.com/> |
| 6   | - **Thực hành (Lab: S3 Static Website, CloudFront và Replication):** <br>&emsp; + Tạo S3 bucket, bật Static Website Hosting, test qua S3 endpoint <br>&emsp; + Block Public Access, cấu hình CloudFront với Origin Access Control (OAC) <br>&emsp; + Bật S3 Versioning, dùng Lifecycle Policy chuyển storage class theo thời gian <br>&emsp; + Cấu hình Cross-Region Replication (CRR) cho disaster recovery <br> - Tổng hợp kiến thức, viết báo cáo tuần 4 | 15/05/2026   | 15/05/2026      | <https://cloudjourney.awsstudygroup.com/> |

### Kết quả đạt được tuần 4:

* Nắm vững Amazon S3: Access Point để đơn giản hóa quản lý quyền truy cập, các Storage Class để tối ưu chi phí, và Lifecycle Policy để tự động hóa vòng đời dữ liệu.
* Hiểu sâu các tính năng nâng cao S3: Static Website Hosting, CORS, nhiều lớp kiểm soát truy cập (Bucket Policy, IAM, ACL, Block Public Access, Pre-signed URL).
* Nắm được vai trò và kịch bản sử dụng của S3 Glacier cho lưu trữ lạnh, compliance archive với Vault Lock.
* Hiểu rõ AWS Snow Family như giải pháp di chuyển dữ liệu ngoại tuyến quy mô lớn – quan trọng khi băng thông mạng là bottleneck.
* Thực hành triển khai AWS Storage Gateway kết nối on-premises với S3, tạo hybrid cloud storage liền mạch.
* Thực hành toàn bộ quy trình VM Import/Export – nền tảng của chiến lược lift-and-shift migration.
* Làm chủ Amazon FSx for Windows: từ triển khai Multi-AZ đến các tính năng enterprise như deduplication, shadow copies, quota và dynamic scaling.
* Xây dựng kiến trúc phân phối nội dung tĩnh chuẩn AWS với S3 + CloudFront + OAC; kết hợp Versioning, Lifecycle và Cross-Region Replication cho chiến lược bảo vệ dữ liệu đa lớp.

### Khó khăn và cách khắc phục:

| Khó khăn gặp phải | Cách khắc phục |
| --- | --- |
| Nhiều Storage Class của S3 (7 loại) dễ gây nhầm lẫn về chi phí và thời gian truy xuất. | Lập bảng so sánh theo chi phí lưu trữ, phí truy xuất và thời gian retrieval để chọn đúng class cho từng loại dữ liệu. |
| Cấu hình S3 Access Point cho nhiều team/VPC cùng chia sẻ một bucket còn khá mới. | Thực hành theo từng use case cụ thể: một Access Point riêng cho mỗi nhóm người dùng với policy đơn giản hơn thay vì một bucket policy phức tạp. |
| Quy trình VM Import/Export có nhiều bước (export OVA/VMDK, upload S3, import AMI, deploy) dễ sai định dạng hoặc thiếu quyền S3. | Làm theo checklist tuần tự từng bước của lab, kiểm tra kỹ cấu hình S3 bucket ACL trước khi export/import. |

### Bài học kinh nghiệm:

* Tính năng thông báo qua SNS đặc biệt quan trọng trong môi trường production để phát hiện lỗi backup kịp thời; cross-account backup là best practice bảo vệ dữ liệu backup khỏi sự cố tài khoản chính.
* VM Import/Export là nền tảng của chiến lược lift-and-shift migration: quy trình thực tế không chỉ đơn giản là copy dữ liệu mà còn bao gồm chuyển đổi định dạng, cấu hình quyền S3 và kiểm tra tính tương thích.
* Storage Gateway cho thấy cách AWS giải quyết hybrid cloud storage thực tế: cache cục bộ đảm bảo hiệu năng cho dữ liệu hot, trong khi backend S3 đảm bảo độ bền và khả năng mở rộng.
* Khả năng scale throughput và storage của FSx mà không cần downtime là ưu điểm vượt trội so với NAS/SAN vật lý truyền thống.
* Kiến trúc S3 + CloudFront + OAC là pattern chuẩn để triển khai Single Page Application và static content trên AWS; S3 Versioning kết hợp Lifecycle Policy và CRR tạo nên chiến lược bảo vệ dữ liệu toàn diện theo nhiều chiều: phiên bản, vòng đời và địa lý.

### Kế hoạch tuần tiếp theo:

* Chuyển sang chủ đề Bảo mật và Quản lý Danh tính trên AWS: Mô hình Shared Responsibility giữa AWS và khách hàng.
* Tìm hiểu sâu AWS IAM (User, Group, Role, Policy), Amazon Cognito, AWS Organization và Service Control Policy, AWS Identity Center (SSO).
* Tìm hiểu Amazon KMS (Key Management Service) và AWS Security Hub cho giám sát bảo mật tập trung.
* Thực hành các lab về Security Hub, tự động hóa EC2 với Lambda, quản lý Tag/Resource Group, IAM nâng cao (Switch Role, Tag-Based Access Control), KMS/CloudTrail/Athena và so sánh IAM Access Key với IAM Role.
