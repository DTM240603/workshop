---
title: "Blog 3"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 3.3. </b> "
---

# Đơn Giản Hóa Tích Hợp AWS AppSync Events Bằng Powertools Cho AWS Lambda

**Tác giả:** Phạm Anh Hào &emsp; | &emsp; **Nhóm:** ITSoldier

Có anh em nào làm app real-time (như chat-chit, push notification, live dashboards, leaderboards...) mà vẫn đang hì hục ngồi tự viết code parse, route và format các WebSocket events trong Lambda không?

Mặc dù tính năng `AppSyncEventsResolver` trong bộ Powertools cho AWS Lambda đã được giới thiệu được một thời gian, nhưng đến nay đây vẫn là một giải pháp cực kỳ xịn sò giúp anh em dẹp bỏ hoàn toàn đống boilerplate code phiền phức để tập trung viết business logic cho app.

### Vấn Đề

Việc xử lý các sự kiện WebSocket trong kiến trúc serverless thường gặp nhiều khó khăn: lập trình viên phải viết rất nhiều code mẫu (boilerplate code) chỉ để phân tích cú pháp (parsing), lọc dữ liệu, định tuyến thủ công các sự kiện đến đúng hàm xử lý, và định dạng lại dữ liệu phản hồi sao cho tương thích với giao thức của AppSync.

### Giải Pháp

Cần một cơ chế tự động hóa việc định tuyến và chuẩn hóa dữ liệu để các nhà phát triển có thể tập trung hoàn toàn vào logic nghiệp vụ thay vì các công việc hạ tầng lặp đi lặp lại. AWS đã giới thiệu tiện ích `AppSyncEventsResolver` nhằm giải quyết triệt để các tác vụ nặng nhọc và không mang lại giá trị khác biệt này.

#### 1. Định tuyến dựa trên Pattern (Pattern-based Routing)

* Tự động định tuyến các sự kiện đầu vào đến các phương thức xử lý thích hợp dựa trên namespace và channel mà không cần cấu trúc switch-case thủ công.
* Hỗ trợ Wildcards giúp cấu hình các hàm xử lý chung cực kỳ linh hoạt.

#### 2. Tự động chuẩn hóa dữ liệu & định dạng phản hồi

* Hỗ trợ đắc lực cho cả hai cơ chế sự kiện publish và subscribe.
* Tự động chuyển đổi và định dạng phản hồi từ Lambda khớp hoàn toàn với cấu trúc gói tin mà AWS AppSync Events yêu cầu.

#### 3. Batch Processing

* Cho phép gộp nhiều sự kiện để xử lý song song hoặc tuần tự, giúp tối ưu hóa hiệu năng và chi phí chạy Lambda.
* Đi kèm cơ chế xử lý lỗi cục bộ cho từng sự kiện đơn lẻ trong lô, đảm bảo một lỗi nhỏ không làm sập toàn bộ luồng xử lý hàng loạt.

Tính năng này được phát hành đồng bộ trên các thư viện Powertools dành cho các ngôn ngữ phổ biến nhất: **Python**, **TypeScript/JavaScript**, và **.NET**.

### Kết Luận

Phát triển ứng dụng real-time quy mô lớn giờ đây đã nằm trong tầm tay của mọi nhà phát triển nhờ sự kết hợp hoàn hảo giữa AWS AppSync Events (lo phần WebSocket scale tự động) và Powertools for AWS Lambda (lo phần giải quyết code rác và xử lý sự kiện). Hãy tận dụng tối đa các thư viện Powertools để giữ cho codebase của Lambda luôn sạch, dễ bảo trì.

**Link bài viết gốc:** [aws.amazon.com/vi/blogs/mobile/simplify-aws-appsync-events-integration...](https://aws.amazon.com/vi/blogs/mobile/simplify-aws-appsync-events-integration-with-powertools-for-aws-lambda/)

**Link bài đã đăng lên nhóm AWS Study Group VN:** [facebook.com/groups/awsstudygroupfcj/permalink/2183284039103223](https://www.facebook.com/groups/awsstudygroupfcj/permalink/2183284039103223/)

![Đơn giản hóa tích hợp AWS AppSync Events bằng Powertools cho AWS Lambda](/images/3-BlogsPosted/3.3-Blog3/1.jpg)
