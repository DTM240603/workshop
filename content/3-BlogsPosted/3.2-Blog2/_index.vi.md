---
title: "Blog 2"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 3.2. </b> "
---

# Amazon OpenSearch Service: Cải thiện tìm kiếm lịch sử đơn hàng bằng Semantic Search

**Tác giả:** Phạm Anh Hào &emsp; | &emsp; **Nhóm:** ITSoldier

Bài phân tích kỹ thuật thực tế về cách đội ngũ Amazon cải tiến tính năng lịch sử mua hàng — hệ thống quản lý hàng tỷ đơn hàng từ năm 1995. Để phục vụ các trợ lý ảo như Rufus và Alexa xử lý các câu hỏi tự nhiên, ví dụ *"Tìm đồ uống lành mạnh tôi mua năm ngoái"*, Amazon đã nâng cấp hệ thống bằng Semantic Search trên nền tảng Amazon OpenSearch Service và Amazon SageMaker.

### Hạn Chế Của Hệ Thống Cũ

Hệ thống cũ dựa trên khớp từ khóa (Lexical Matching – BM25).

* **Vấn đề:** Chỉ hoạt động tốt khi nhập đúng tên sản phẩm. Nếu tìm kiếm cụm từ mang ý nghĩa chung như "healthy drinks", hệ thống sẽ bỏ sót "kombucha" hay "trà xanh" vì tiêu đề của chúng không chứa từ khóa này.
* **Giải pháp:** Cần Semantic Search để hiểu được ngữ nghĩa và ý định thực tế của người dùng.

### Thử Thách

* **Quy mô khổng lồ:** Xử lý và tìm kiếm vector trên hàng tỷ bản ghi tích lũy.
* **Zero Downtime:** Đảm bảo hệ thống hoạt động 100% liên tục trong quá trình nâng cấp.
* **Chất lượng tìm kiếm:** Tránh làm loãng kết quả khi người dùng tìm kiếm chính xác (ví dụ tìm "iPhone 15") và xử lý các mã định danh không mang ngữ nghĩa như Order ID (trong trường hợp này vẫn dùng Lexical Search).

### Giải Pháp

Để giải quyết bài toán trên, Amazon chia giải pháp thành hai phần chính:

#### 1. Nâng cao khả năng chịu tải với Cell-Based Architecture

* Hệ thống được chia nhỏ thành các phân cụm độc lập gọi là các **cells**, mỗi cell phục vụ một lượng khách hàng riêng biệt.
* Định tuyến yêu cầu được thực hiện linh hoạt dựa trên bộ nhớ đệm hoặc Amazon DynamoDB.
* Nếu một cell gặp sự cố, hệ thống chỉ bị giảm công suất theo tỉ lệ tương đương (**Blast Radius** giới hạn trong phạm vi cell đó) thay vì sập toàn bộ. Dữ liệu cũng được ghi dự phòng đa cell để tránh mất mát.

#### 2. Triển khai Semantic Search

* Sử dụng phương pháp **LLM-as-a-judge** với Anthropic's Claude trên Amazon Bedrock để chấm điểm các mô hình ứng cử viên dựa trên các chỉ số NDCG, MRR, Precision và Recall.
* Đóng gói mô hình và triển khai qua **Amazon SageMaker Inference Endpoints** kết hợp Amazon Elastic Container Registry.
* Sử dụng trường `knn_vector` trong OpenSearch. Vì số lượng đơn hàng của mỗi khách hàng có giới hạn, hệ thống chạy thuật toán exact k-NN trực tiếp trên server bằng Scripted Scoring để tối ưu độ chính xác và tốc độ.
* Hệ thống kết hợp chạy song song cả Lexical Search và Semantic Search: kết quả từ hai luồng được gộp, chuẩn hóa điểm số và trả về cho người dùng. Nếu người dùng tìm kiếm bằng mã định danh (như Order ID), hệ thống tự động bỏ qua Semantic Search. Nếu luồng vector gặp sự cố, hệ thống tự động fallback về Lexical Search truyền thống, đảm bảo khách hàng luôn nhận được kết quả.

#### Quy trình cập nhật dữ liệu cũ

Để Semantic Search có hiệu lực với các đơn hàng cũ, Amazon xây dựng pipeline xử lý dữ liệu quy mô lớn sử dụng **AWS Step Functions** điều phối và **AWS Lambda** thực thi để tạo vector nhúng cho hàng tỷ bản ghi cũ mà không ảnh hưởng tới hiệu năng hệ thống hiện tại.

### Tác Động Đến Doanh Nghiệp

* Tìm kiếm thông minh hơn (ví dụ tìm "dụng cụ ăn uống bền vững" sẽ ra "thìa gỗ" dù không trùng từ khóa).
* Tăng 10% Query Recall và tăng 20% tỷ lệ tìm kiếm thành công.
* Mở rộng 48% Result Coverage, giúp Rufus và Alexa hoạt động hiệu quả hơn.

### Kiến Thức Học Được

Qua bài viết, mình học được rằng việc cải tiến tìm kiếm không chỉ dừng lại ở việc áp dụng công nghệ mới. Khả năng chịu tải của hạ tầng và việc duy trì tính ổn định của hệ thống hiện tại cũng cực kỳ quan trọng để đảm bảo trải nghiệm người dùng không bị gián đoạn.

Semantic Search và Hybrid Search là những giải pháp hữu ích giúp Amazon OpenSearch Service cung cấp trải nghiệm tìm kiếm thông minh hơn dựa trên ý định thực tế của khách hàng thay vì chỉ đối chiếu khớp từ khóa thô sơ như trước đây.

**Link bài viết gốc:** [aws.amazon.com/vi/blogs/big-data/improving-order-history-search...](https://aws.amazon.com/vi/blogs/big-data/improving-order-history-search-using-semantic-search-with-amazon-opensearch-service/)

**Link bài đã đăng lên nhóm AWS Study Group VN:** [facebook.com/groups/awsstudygroupfcj/permalink/2177864399645187](https://www.facebook.com/groups/awsstudygroupfcj/permalink/2177864399645187/)

![Cell-Based Architecture và Semantic Search trên Amazon OpenSearch Service](/images/3-BlogsPosted/3.2-Blog2/1.jpg)

![Kiến trúc kết hợp Lexical Search và Semantic Search](/images/3-BlogsPosted/3.2-Blog2/2.jpg)

![Pipeline cập nhật embedding vector với AWS Step Functions và Lambda](/images/3-BlogsPosted/3.2-Blog2/3.jpg)

![Kết quả cải thiện Query Recall và Result Coverage](/images/3-BlogsPosted/3.2-Blog2/4.jpg)
