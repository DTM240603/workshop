---
title: "Worklog Tuần 1"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 1.1. </b> "
---

**Họ và tên:** Đinh Tuấn Minh &emsp; | &emsp; **MSSV:** 2280601918

**Người hướng dẫn tại đơn vị thực tập:** Nguyễn Gia Hưng – Head of Solution Architect &emsp; | &emsp; **Giảng viên hướng dẫn:** Võ Phạm Thành Luân

### Mục tiêu tuần 1:

- Nắm được khái niệm nền tảng về điện toán đám mây, mô hình sử dụng tài nguyên trên nền tảng cloud và vai trò của AWS trong hạ tầng công nghệ hiện đại.
- Làm quen với hệ sinh thái AWS, bao gồm các nhóm dịch vụ cốt lõi, hạ tầng toàn cầu, công cụ quản lý dịch vụ, cơ chế xác thực tài khoản và nguyên tắc quản trị chi phí.
- Thực hành các lab cơ bản trên AWS như tạo tài khoản, thiết lập MFA, tạo nhóm/người dùng quản trị, cấu hình ngân sách chi phí và tìm hiểu AWS Support.

### Các công việc cần triển khai trong tuần này:

| Thứ | Công việc                                                                                                                                                                                                                                                                                                                      | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu                            |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------ | --------------- | ----------------------------------------- |
| 2   | - Làm quen với các thành viên FCAJ, đọc nội quy đơn vị thực tập <br> - Điều gì tạo nên sự khác biệt của AWS?                                                                                                                                                                                                                   | 20/04/2026   | 20/04/2026      |                                           |
| 3   | - Bắt đầu hành trình lên mây như thế nào <br> - Hạ tầng toàn cầu của AWS <br> - Công cụ quản lý AWS Services                                                                                                                                                                                                                   | 21/04/2026   | 21/04/2026      | <https://cloudjourney.awsstudygroup.com/> |
| 4   | - Tối ưu hóa chi phí trên AWS và làm việc với AWS Support <br> - **Thực hành:** <br>&emsp; + Setup with Virtual MFA Device <br>&emsp; + Create admin group and admin user <br>&emsp; + Account authentication support                                                                                                          | 22/04/2026   | 22/04/2026      | <https://cloudjourney.awsstudygroup.com/> |
| 5   | - Thực hành và nghiên cứu bổ sung <br> - **Thực hành (AWS Budgets):** <br>&emsp; + Create Budget by Template <br>&emsp; + Create Cost Budget Tutorial <br>&emsp; + Creating a Usage Budget <br>&emsp; + Creating a Reservation Instance (RI) Budget <br>&emsp; + Creating a Savings Plans Budget <br>&emsp; + Clean Up Budgets | 23/04/2026   | 23/04/2026      | <https://cloudjourney.awsstudygroup.com/> |
| 6   | - **Thực hành (AWS Support):** <br>&emsp; + AWS Support Packages <br>&emsp; + Types of support requests <br>&emsp; + Change support package <br>&emsp; + Manage support requests <br> - Tổng hợp kiến thức, viết báo cáo tuần 1                                                                                                | 24/04/2026   | 24/04/2026      | <https://cloudjourney.awsstudygroup.com/> |

### Kết quả đạt được tuần 1:

- Hoàn thành việc học các nội dung tổng quan trong tuần 1, có cái nhìn hệ thống hơn về điện toán đám mây và các thành phần nền tảng của AWS.
- Hiểu được vai trò của IAM, MFA và phân quyền người dùng trong việc bảo mật tài khoản AWS — đây là lớp kiểm soát đầu tiên khi vận hành hệ thống cloud.
- Biết cách tiếp cận quản trị chi phí trên AWS thông qua AWS Budgets, Cost Budget, Usage Budget, RI Budget và Savings Plans Budget, hình thành tư duy FinOps cơ bản.
- Làm quen với AWS Support Center, các loại support request và quy trình xử lý yêu cầu hỗ trợ trong môi trường AWS.

### Khó khăn và cách khắc phục:

| Khó khăn gặp phải                                                                                                                                     | Cách khắc phục                                                                                                                                  |
| ----------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------- |
| Một số khái niệm ban đầu như Region, Availability Zone, IAM, Budget và Support Package còn dễ nhầm lẫn do liên quan đến nhiều nhóm dịch vụ khác nhau. | Ghi chú lại từng khái niệm theo dạng bảng so sánh, phân biệt chức năng, mục đích sử dụng và ví dụ thực tế.                                      |
| Giao diện AWS Console có nhiều mục cấu hình nên cần thời gian để làm quen luồng thao tác.                                                             | Thực hiện lab từng bước, đối chiếu với video hướng dẫn và ghi lại các bước quan trọng để có thể tự làm lại.                                     |
| Nội dung tối ưu chi phí còn mới, đặc biệt là Reserved Instance và Savings Plans.                                                                      | Tìm hiểu thêm về mô hình tính phí AWS, phân biệt On-Demand, Reserved Instance và Savings Plans ở mức khái niệm trước khi đi sâu vào triển khai. |

### Bài học kinh nghiệm:

- Khi làm việc với cloud, cần ưu tiên bảo mật tài khoản ngay từ đầu, đặc biệt là bật MFA và không sử dụng root account cho các thao tác hằng ngày.
- Quản trị chi phí là kỹ năng bắt buộc khi học AWS. Việc tạo budget và cảnh báo chi phí giúp hạn chế rủi ro phát sinh chi phí ngoài dự kiến trong quá trình thực hành.
- Muốn học AWS hiệu quả cần kết hợp giữa lý thuyết kiến trúc cloud, thao tác lab trên console và ghi chú lại quy trình để hình thành tư duy triển khai thực tế.

### Kế hoạch tuần tiếp theo:

- Tiếp tục chương trình Bootcamp First Cloud AI Journey, chuyển sang nội dung về Amazon Virtual Private Cloud (VPC) và các mô hình kết nối mạng trên AWS.
- Tìm hiểu cách thiết kế mạng riêng ảo: CIDR block, subnet, route table, Internet Gateway, NAT Gateway và các thành phần bảo mật mạng (Security Group, Network ACLs).
- Tìm hiểu các mô hình kết nối nâng cao: VPN, Direct Connect, Load Balancer, Route 53 Resolver, VPC Peering và Transit Gateway.
- Thực hành triển khai VPC, Hybrid DNS, VPC Peering và Transit Gateway qua các lab thực hành trên AWS Console.
