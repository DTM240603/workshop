---
title: "Blog 1"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 3.1. </b> "
---

# Giám Sát và Điều Tra Bảo Mật S3 với AWS CloudTrail và Amazon Athena

**Tác giả:** Đinh Tuấn Minh &emsp; | &emsp; **Nhóm:** ITSoldier

Khi một sự cố bảo mật xảy ra trên Amazon S3 — có thể là một file bị xóa hàng loạt, một tài khoản lạ tải dữ liệu xuống, hay một truy cập đến từ IP không xác định — câu hỏi đầu tiên luôn là: *"Ai đã làm điều này?"* Server access logs chỉ cho biết có request xảy ra, nhưng không trả lời được: đó là user nào, role nào, có bật MFA không, hay request đến từ trong hay ngoài tổ chức. Thiếu những thông tin này, quá trình điều tra trở nên chậm chạp và rủi ro compliance ngày càng cao.

AWS CloudTrail Data Events kết hợp với Amazon Athena chính là giải pháp để lấp đầy khoảng trống đó, ghi lại đầy đủ danh tính người thực hiện mọi thao tác trên S3 và cho phép truy vấn hàng triệu sự kiện trong vài giây mà không cần provisioning infrastructure.

### 1. Tổng Quan Giải Pháp

Giải pháp này kết hợp ba dịch vụ AWS để tạo ra một nền tảng điều tra bảo mật S3 toàn diện:

* **AWS CloudTrail Data Events:** Ghi lại mọi API call trên S3 (GetObject, PutObject, DeleteObject,...) kèm đầy đủ thông tin định danh: IAM user/role, trạng thái MFA, source IP, user agent và thông tin cross-account access. Khác với server access logs chỉ ghi thông tin HTTP, CloudTrail trả lời câu hỏi "ai làm gì" ở cấp độ identity.
* **Amazon S3 (Centralized Log Bucket):** Tập trung log từ nhiều tài khoản AWS về một bucket duy nhất, tổ chức theo cấu trúc partition theo account/region/ngày để tối ưu chi phí query về sau.
* **Amazon Athena với Partition Projection:** Cho phép viết SQL query trực tiếp trên log JSON lưu trong S3 mà không cần ETL hay database. Partition projection tự động nhận diện cấu trúc thư mục, giúp giảm lượng data scan và tiết kiệm chi phí đáng kể.

### 2. Lợi Ích Cốt Lõi

* **Điều tra theo danh tính:** Biết chính xác IAM user, role hay federated identity nào đã thực hiện thao tác, kể cả các trường hợp cross-account access hay assume role phức tạp.
* **Phát hiện truy cập bất thường:** Dễ dàng query để tìm các lần AccessDenied, xóa file hàng loạt, hay truy cập từ IP lạ trong vài giây.
* **Audit compliance:** Có đầy đủ bằng chứng về ai truy cập dữ liệu nhạy cảm và khi nào, phục vụ các yêu cầu HIPAA, PCI DSS hay SOC 2.
* **Serverless, không cần hạ tầng:** Athena tự động scale theo workload, chỉ trả tiền theo lượng data scan thực tế.

### 3. Hướng Dẫn Triển Khai

**Bước 1 – Bật CloudTrail Data Events cho S3:** Vào CloudTrail Console, tạo trail mới với tên như `s3-data-events-trail`. Chọn S3 bucket đích để lưu log, bật SSE-KMS encryption và log file validation. Ở phần Log events, bỏ chọn Management events (để tránh tính phí trùng nếu đã có trail khác) và chỉ chọn Data events → S3. Với Advanced event selectors, có thể lọc theo prefix bucket hoặc loại bỏ các event ít giá trị như HeadObject để giảm chi phí.

**Bước 2 – Tập trung log về một bucket duy nhất:** Nếu có nhiều AWS account, cấu hình Organization Trail từ Management Account với tùy chọn "Enable for all accounts in my organization". CloudTrail sẽ tự động thu thập log từ toàn bộ member accounts và gửi về một S3 bucket trung tâm, tổ chức theo cấu trúc `AWSLogs/{organization_id}/{account_id}/CloudTrail/{region}/{year}/{month}/{day}/`.

**Bước 3 – Tạo Athena table với Partition Projection:** Tạo database và table trong Athena trỏ đến S3 bucket chứa CloudTrail log. Dùng Partition Projection để Athena tự động nhận diện cấu trúc thư mục theo account/region/ngày, không cần chạy `MSCK REPAIR TABLE` thủ công và query sẽ chỉ scan đúng partition cần thiết, giảm chi phí đến 90% so với full scan.

**Bước 4 – Phân tích với SQL query:** Sau khi table được tạo, có thể chạy các query điều tra thực tế như: tìm tất cả lần xóa file trong một ngày cụ thể, theo dõi hoạt động của một IAM user, phát hiện access từ ngoài tổ chức, hay liệt kê các lần AccessDenied. Một best practice quan trọng là luôn filter theo partition (account, region, ngày) trước các điều kiện khác để Athena chỉ scan lượng data tối thiểu.

### 4. Kết Luận

Bằng cách kết hợp CloudTrail Data Events để ghi lại danh tính đầy đủ và Amazon Athena để truy vấn serverless, tổ chức có thể xây dựng một hệ thống điều tra bảo mật S3 mạnh mẽ mà không cần infrastructure phức tạp. Mỗi lần ai đó đụng vào dữ liệu trên S3, dù là upload, download hay xóa, đều để lại dấu vết rõ ràng với đầy đủ thông tin danh tính, sẵn sàng để điều tra bất cứ lúc nào.

**Link bài viết gốc:** [aws.amazon.com/blogs/storage/amazon-s3-audit-logging-part-2](https://aws.amazon.com/blogs/storage/amazon-s3-audit-logging-part-2-centralized-logging-and-analysis-of-s3-data-events-in-aws-cloudtrail-for-security-and-compliance/)

**Link bài đã đăng lên nhóm AWS Study Group VN:** [facebook.com/groups/awsstudygroupfcj/permalink/2183659809065646](https://www.facebook.com/groups/awsstudygroupfcj/permalink/2183659809065646/)

![Giám sát và điều tra bảo mật S3 với CloudTrail và Athena](/images/3-BlogsPosted/3.1-Blog1/1.jpg)
