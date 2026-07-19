---
title: "Worklog Tuần 2"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 1.2. </b> "
---

**Họ và tên:** Đinh Tuấn Minh &emsp; | &emsp; **MSSV:** 2280601918

**Người hướng dẫn tại đơn vị thực tập:** Nguyễn Gia Hưng – Head of Solution Architect &emsp; | &emsp; **Giảng viên hướng dẫn:** Võ Phạm Thành Luân

### Mục tiêu tuần 2:

* Nắm được kiến thức nền tảng về Amazon Virtual Private Cloud (VPC), bao gồm cách thiết kế mạng riêng ảo, phân chia subnet, định tuyến và kết nối Internet cho tài nguyên AWS.
* Hiểu các thành phần bảo mật mạng trong VPC như Security Group, Network ACLs, cơ chế kiểm soát inbound/outbound traffic và cách tổ chức kiến trúc multi-VPC.
* Thực hành xây dựng các mô hình kết nối mạng trên AWS như NAT Gateway, EC2 Instance Connect Endpoint, Route 53 Resolver, VPC Peering và Transit Gateway.
* Hình thành tư duy thiết kế network architecture trên cloud theo hướng an toàn, có khả năng mở rộng và dễ quản trị.

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc                                                                                                                                                                                                                    | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu                            |
| --- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ----------------------------------------- |
| 2   | - AWS Virtual Private Cloud: CIDR block, subnet, route table, Internet Gateway, NAT Gateway, phân tách public/private subnet <br> - VPC Security và Multi-VPC: Security Group, Network ACLs, VPC Peering, Transit Gateway <br> - VPN, Direct Connect, Load Balancer và các tài nguyên bổ sung | 27/04/2026   | 27/04/2026      | <https://cloudjourney.awsstudygroup.com/> |
| 3   | - **Thực hành VPC cơ bản:** <br>&emsp; + Tìm hiểu Subnet, Route table, Internet Gateway, NAT Gateway <br>&emsp; + Thực hành Security Group và Network ACLs, quan sát VPC Resource Map <br>&emsp; + Tạo VPC, Subnet, Internet Gateway, Route table và Security Group <br>&emsp; + Tạo EC2 instance trong subnet và kiểm tra kết nối <br>&emsp; + Tạo NAT Gateway và EC2 Instance Connect Endpoint | 28/04/2026   | 28/04/2026      | <https://cloudjourney.awsstudygroup.com/> |
| 4   | - **Thực hành Hybrid DNS với Route 53 Resolver:** <br>&emsp; + Tạo Key Pair, khởi tạo CloudFormation template, cấu hình Security Group <br>&emsp; + Kết nối RDGW và thiết lập DNS <br>&emsp; + Tạo Route 53 Outbound Endpoint, Resolver Rules và Inbound Endpoint <br>&emsp; + Kiểm thử kết quả và dọn dẹp tài nguyên | 29/04/2026   | 29/04/2026      | <https://cloudjourney.awsstudygroup.com/> |
| 5   | - **Thực hành VPC Peering:** <br>&emsp; + Khởi tạo CloudFormation, tạo Security Group và EC2 instance <br>&emsp; + Cập nhật Network ACL, tạo Peering Connection <br>&emsp; + Cấu hình Route table và bật Cross-Peer DNS <br>&emsp; + Dọn dẹp tài nguyên | 30/04/2026   | 30/04/2026      | <https://cloudjourney.awsstudygroup.com/> |
| 6   | - **Thực hành AWS Transit Gateway:** <br>&emsp; + Chuẩn bị tài nguyên, tạo Transit Gateway <br>&emsp; + Tạo Transit Gateway Attachments và Route Tables <br>&emsp; + Cập nhật VPC Route Tables, dọn dẹp tài nguyên <br> - Tổng hợp kiến thức, viết báo cáo tuần 2 | 01/05/2026   | 01/05/2026      | <https://cloudjourney.awsstudygroup.com/> |

### Kết quả đạt được tuần 2:

* Hoàn thành phần lý thuyết trọng tâm về Amazon VPC, hiểu rõ hơn vai trò của VPC trong thiết kế hạ tầng mạng trên AWS.
* Biết cách phân biệt và sử dụng các thành phần mạng chính như VPC, subnet, route table, Internet Gateway, NAT Gateway, Security Group và Network ACLs.
* Thực hành triển khai mô hình public/private subnet, cấu hình outbound Internet routing, kiểm thử kết nối EC2 và hiểu cách bảo vệ tài nguyên trong private subnet.
* Nắm được mô hình Hybrid DNS với Route 53 Resolver, bao gồm inbound endpoint, outbound endpoint và resolver rule.
* Hiểu sự khác nhau giữa VPC Peering và Transit Gateway: VPC Peering phù hợp kết nối point-to-point, còn Transit Gateway phù hợp mô hình hub-and-spoke khi có nhiều VPC cần kết nối tập trung.
* Rèn luyện tư duy dọn dẹp tài nguyên sau lab để tránh phát sinh chi phí không cần thiết.

### Khó khăn và cách khắc phục:

| Khó khăn gặp phải | Cách khắc phục |
| --- | --- |
| Dễ nhầm lẫn giữa Security Group và Network ACL vì cả hai đều liên quan đến kiểm soát traffic. | Lập bảng so sánh: Security Group hoạt động ở cấp instance/ENI và stateful; Network ACL hoạt động ở cấp subnet và stateless. |
| Cấu hình route table có nhiều trường hợp khác nhau như route qua IGW, NAT Gateway, VPC Peering hoặc Transit Gateway. | Ghi chú theo sơ đồ luồng traffic: nguồn, đích, next hop và subnet áp dụng để tránh cấu hình sai route. |
| Các khái niệm Hybrid DNS, inbound/outbound endpoint và resolver rule còn mới. | Vẽ lại mô hình truy vấn DNS theo chiều đi của request để hiểu rõ endpoint nào nhận/trả lời truy vấn. |
| Khi thực hành nhiều lab, số lượng tài nguyên tạo ra khá nhiều, dễ bỏ sót khi clean up. | Kiểm tra lại từng nhóm tài nguyên sau lab như EC2, NAT Gateway, VPC endpoint, Route 53 Resolver endpoint, peering connection và Transit Gateway attachment. |

### Bài học kinh nghiệm:

* Khi thiết kế mạng trên AWS, cần xác định rõ mục tiêu của từng subnet trước khi triển khai: subnet nào public, subnet nào private, subnet nào dùng cho endpoint hoặc tài nguyên nội bộ.
* Route table là thành phần quyết định đường đi của traffic. Chỉ tạo gateway hoặc peering connection là chưa đủ, cần cấu hình route đúng ở cả hai chiều nếu muốn kết nối hoạt động ổn định.
* Bảo mật mạng cần triển khai theo nhiều lớp. Security Group giúp kiểm soát ở cấp instance, còn Network ACL bổ sung lớp kiểm soát ở cấp subnet.
* Với hệ thống nhiều VPC, cần chọn mô hình kết nối phù hợp. VPC Peering đơn giản cho ít VPC, nhưng Transit Gateway dễ quản trị hơn khi số lượng VPC tăng lên.
* Luôn clean up tài nguyên sau khi thực hành, đặc biệt là NAT Gateway, Transit Gateway và Route 53 Resolver Endpoint vì đây là các tài nguyên có thể phát sinh chi phí nếu để tồn tại lâu.

### Kế hoạch tuần tiếp theo:

* Tiếp tục chương trình Bootcamp First Cloud AI Journey, chuyển sang nội dung về Dịch vụ Compute và Storage trên AWS.
* Tìm hiểu Amazon EC2: Instance Type, AMI, EBS, Instance Store, User Data và EC2 Auto Scaling.
* Tìm hiểu các dịch vụ mở rộng: Amazon EFS, FSx, Lightsail và AWS MGN (Application Migration Service).
* Thực hành các lab về AWS Backup, AWS Storage Gateway, và triển khai website tĩnh trên S3 kết hợp Amazon CloudFront.
