---
title: "Worklog Tuần 3"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 1.3. </b> "
---

**Họ và tên:** Đinh Tuấn Minh &emsp; | &emsp; **MSSV:** 2280601918

**Người hướng dẫn tại đơn vị thực tập:** Nguyễn Gia Hưng – Head of Solution Architect &emsp; | &emsp; **Giảng viên hướng dẫn:** Võ Phạm Thành Luân

**Chủ đề:** Dịch vụ Compute và Storage trên AWS

### Mục tiêu tuần 3:

* Nắm vững kiến trúc và các tùy chọn cấu hình của Amazon EC2: Instance Type, AMI, EBS, Instance Store, User Data và EC2 Auto Scaling.
* Hiểu vai trò của các dịch vụ lưu trữ mở rộng: Amazon EFS, FSx, Lightsail và AWS MGN (Application Migration Service).
* Thực hành triển khai và quản lý AWS Backup để xây dựng chiến lược bảo vệ dữ liệu.
* Thiết lập hybrid storage với AWS Storage Gateway và triển khai website tĩnh trên S3 tích hợp CloudFront theo best practice bảo mật.

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc                                                                                                                                                                                                                    | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu                            |
| --- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ----------------------------------------- |
| 2   | - Amazon EC2 – Instance Type: các họ instance (General Purpose, Compute/Memory/Storage Optimized, Accelerated Computing) <br> - AMI, Backup (EBS Snapshot) và Key Pair <br> - Amazon EBS: đặc điểm và các loại volume (gp3/gp2, io2/io1, st1, sc1) | 04/05/2026   | 04/05/2026      | <https://cloudjourney.awsstudygroup.com/> |
| 3   | - Instance Store: đặc điểm, trường hợp mất dữ liệu và ứng dụng phù hợp <br> - EC2 User Data: cơ chế bootstrapping, ví dụ script cài đặt web server <br> - EC2 Auto Scaling: Launch Template, Auto Scaling Group, các loại Scaling Policy | 05/05/2026   | 05/05/2026      | <https://cloudjourney.awsstudygroup.com/> |
| 4   | - Các dịch vụ mở rộng: Amazon EFS, Amazon FSx (Windows/Lustre/NetApp ONTAP), Amazon Lightsail, AWS MGN <br> - **Thực hành (Lab: AWS Backup):** <br>&emsp; + Triển khai hạ tầng EC2/EBS qua CloudFormation <br>&emsp; + Tạo Backup Plan, gán tài nguyên cần backup <br>&emsp; + Test restore từ recovery point, dọn dẹp tài nguyên | 06/05/2026   | 06/05/2026      | <https://cloudjourney.awsstudygroup.com/> |
| 5   | - **Thực hành (Lab: S3 và Storage Gateway):** <br>&emsp; + Tạo S3 bucket làm backend lưu trữ <br>&emsp; + Khởi chạy EC2 mô phỏng thiết bị on-premises gateway <br>&emsp; + Kích hoạt và cấu hình Storage Gateway kết nối S3 <br>&emsp; + Tạo File Share (SMB/NFS) để client mount và truy cập dữ liệu | 07/05/2026   | 07/05/2026      | <https://cloudjourney.awsstudygroup.com/> |
| 6   | - **Thực hành (Lab: S3 Static Website và Amazon CloudFront):** <br>&emsp; + Tạo S3 bucket, upload nội dung website tĩnh, bật Static Website Hosting <br>&emsp; + Cấu hình Bucket Policy public để test qua S3 endpoint <br>&emsp; + Block Public Access, tạo CloudFront Distribution với Origin Access Control (OAC) <br>&emsp; + Thực hành S3 Lifecycle Policy và Cross-Region Replication (CRR) <br> - Tổng hợp kiến thức, viết báo cáo tuần 3 | 08/05/2026   | 08/05/2026      | <https://cloudjourney.awsstudygroup.com/> |

### Kết quả đạt được tuần 3:

* Nắm vững kiến trúc và các tùy chọn cấu hình của Amazon EC2: Instance Type, AMI, EBS, Instance Store, User Data, Auto Scaling.
* Hiểu rõ sự khác biệt giữa các loại storage: EBS (block storage bền vững), Instance Store (ephemeral storage tốc độ cao), EFS (shared file storage).
* Thực hành triển khai và quản lý AWS Backup, xây dựng chiến lược bảo vệ dữ liệu.
* Thiết lập hybrid storage với AWS Storage Gateway, kết nối on-premises với AWS S3.
* Triển khai website tĩnh trên S3 và tích hợp CloudFront CDN theo đúng best practice bảo mật.
* Thực hành Cross-Region Replication cho chiến lược multi-region và disaster recovery.
* Đặt nền tảng quan trọng cho việc thiết kế kiến trúc hệ thống cloud theo AWS Well-Architected Framework, đặc biệt là hai trụ cột Reliability và Performance Efficiency.

### Khó khăn và cách khắc phục:

| Khó khăn gặp phải | Cách khắc phục |
| --- | --- |
| Nhiều loại EBS Volume (gp3, io2, st1, sc1) và Storage Class dễ gây nhầm lẫn khi lựa chọn cho từng workload. | Lập bảng so sánh theo tiêu chí hiệu năng, IOPS và chi phí để chọn đúng loại volume cho từng use case. |
| Dễ nhầm lẫn giữa Instance Store và EBS về tính bền vững dữ liệu. | Ghi chú rõ các trường hợp mất dữ liệu (stop, terminate, host failure) để tránh lưu dữ liệu quan trọng sai chỗ. |
| Quy trình cấu hình CloudFront + Origin Access Control (OAC) để chặn truy cập trực tiếp vào S3 có nhiều bước, dễ sai thứ tự. | Thực hiện tuần tự theo lab: bật Static Website → test qua S3 endpoint → Block Public Access → cấu hình OAC → test lại qua CloudFront. |

### Bài học kinh nghiệm:

* Kiểm tra restore định kỳ là yếu tố quan trọng trong kế hoạch Business Continuity, không chỉ tạo backup mà còn phải xác nhận backup dùng được.
* AWS Storage Gateway cho phép kết hợp hạ tầng on-premises với AWS cloud một cách liền mạch: dữ liệu cache cục bộ giúp giảm độ trễ, trong khi dữ liệu thực sự được lưu bền vững trên S3.
* Kiến trúc S3 + CloudFront + OAC là pattern chuẩn để triển khai static website và Single Page Application trên AWS, vừa cải thiện hiệu năng vừa tăng cường bảo mật cho S3 origin.
* Cross-Region Replication là nền tảng của chiến lược Multi-Region Availability cho các ứng dụng yêu cầu độ sẵn sàng cao.

### Kế hoạch tuần tiếp theo:

* Đi sâu vào hệ sinh thái dịch vụ lưu trữ của AWS: Amazon S3 Access Point, các Storage Class nâng cao và S3 Lifecycle Policy.
* Tìm hiểu các tính năng nâng cao của S3: Static Website Hosting, CORS, các lớp kiểm soát truy cập (Bucket Policy, IAM Policy, ACL, Block Public Access, Pre-signed URL) và Amazon S3 Glacier.
* Tìm hiểu AWS Snow Family cho di chuyển dữ liệu ngoại tuyến quy mô lớn, cùng AWS Storage Gateway và AWS Backup ở mức nâng cao.
* Thực hành các lab: AWS Backup có notification, VM Import/Export, AWS Storage Gateway, Amazon FSx for Windows File Server và S3 Static Website/CloudFront/Replication toàn diện.
