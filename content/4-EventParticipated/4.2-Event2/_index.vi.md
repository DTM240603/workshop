---
title: "Event 2"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 4.2. </b> "
---

# Bài thu hoạch "First Cloud AI Journey Community Day"

**Thời gian:** 09:00 ngày 13/06/2026 &emsp; | &emsp; **Địa điểm:** Tầng 26, tòa nhà Bitexco Financial Tower – AWS Office, TP. Hồ Chí Minh

### Mục Đích Của Sự Kiện

- Tạo không gian giao lưu, chia sẻ kiến thức và kết nối giữa các học viên bootcamp, cựu học viên, AWS Community Builder và kỹ sư đang làm việc trong ngành.
- Truyền cảm hứng về con đường phát triển sự nghiệp cloud thông qua câu chuyện thực tế của người đi trước.
- Chia sẻ kinh nghiệm thiết kế hệ thống thực tế quy mô lớn trên AWS.
- Cung cấp góc nhìn về văn hóa làm việc và cơ hội nghề nghiệp tại các tập đoàn đa quốc gia.

### Danh Sách Diễn Giả

- **Danh Hoàng Hiếu Nghị** – AI Engineer, AWS Community Builder, AWS Student Builder Group Leader
- **Đinh Trung Kiên** và **Nguyễn Minh Thọ** – học viên FCJ, tác giả dự án URL Shortening Service
- **Mr. Đạt Phạm** – Data Analytics Engineer
- **Mr. Cường Nguyễn** – Manufacturing Excellence Engineer

### Nội Dung Nổi Bật

#### Bài thuyết trình 1: "From First Cloud AI Journey to AWS Partner"

Diễn giả **Danh Hoàng Hiếu Nghị** chia sẻ hành trình cá nhân từ một sinh viên tò mò về công nghệ đến khi trở thành AWS Partner thông qua chương trình First Cloud AI Journey, theo lộ trình **8 bước**:

1. **Student Curiosity** – Bắt đầu với sự tò mò
2. **First Cloud Journey** – Tìm môi trường học tập phù hợp
3. **Workshop & Community** – Học hỏi từ người khác
4. **Hands-on Labs** – Học bằng thực hành
5. **School Projects** – Ứng dụng vào bài toán thực tế
6. **Portfolio** – Thể hiện năng lực
7. **AWS Partner** – Giải quyết bài toán của thế giới thực
8. **Share Back** – Giúp đỡ thế hệ tiếp theo

Lộ trình cho thấy con đường từ sinh viên đến AWS Partner không phải bước nhảy vọt đột ngột mà có lộ trình rõ ràng. Bước "Share Back" đặc biệt nhấn mạnh tầm quan trọng của đóng góp cộng đồng.

![From First Cloud AI Journey to AWS Partner](/images/4-EventParticipated/4.2-Event2/1-from-fcj-to-aws-partner.jpg)

#### Bài thuyết trình 2: "A Scalable URL Shortening Service on AWS"

Diễn giả **Đinh Trung Kiên** và **Nguyễn Minh Thọ** trình bày dự án cuối khóa: xây dựng dịch vụ rút gọn URL có khả năng mở rộng cao, xử lý hàng triệu redirect request mỗi ngày với latency thấp. Kiến trúc gồm API Gateway + Lambda (tạo short URL), CloudFront + Lambda@Edge (redirect), DynamoDB (lưu mapping) và ElastiCache Redis (caching). Bốn nguyên tắc thiết kế cốt lõi được tổng kết ở phần Summary:

- **Separation of Concerns**: Tách biệt hoàn toàn read path và write path, mỗi path tối ưu riêng thay vì dùng chung một bottleneck.
- **Defense at the Edge**: Bảo mật và caching đẩy ra CloudFront/WAF, chặn mối đe dọa ngay tại edge trước khi chạm tới core system.
- **Pre-computation over On-demand**: Short code được tạo sẵn và xếp hàng, đảm bảo tạo URL tức thì và không bị collision dưới tải cao.
- **Cache-aside Pattern**: Redirect kiểm tra Redis cache trước, chỉ query DynamoDB khi cache miss, giúp database chịu tải tối thiểu.

![A Scalable URL Shortening Service on AWS](/images/4-EventParticipated/4.2-Event2/2-url-shortening-service.jpg)

#### Bài thuyết trình 3: "Câu chuyện thực tế đến văn hóa tại tập đoàn đa quốc gia"

**Mr. Đạt Phạm** (Data Analytics Engineer) chia sẻ về hành trình trở thành data analyst: cách học, cách tiếp cận và phân tích dữ liệu trong môi trường doanh nghiệp thực tế. **Mr. Cường Nguyễn** (Manufacturing Excellence Engineer) chia sẻ về văn hóa làm việc tại tập đoàn đa quốc gia: kỹ năng tiếng Anh chuyên nghiệp, tư duy làm việc nhóm phân tán, khả năng thích nghi với các phong cách làm việc khác nhau, và lời khuyên xây dựng portfolio, tham gia cộng đồng kỹ thuật ngay từ khi còn là sinh viên.

![Câu chuyện thực tế đến văn hóa tại tập đoàn đa quốc gia](/images/4-EventParticipated/4.2-Event2/3-cau-chuyen-van-hoa.jpg)

### Những Gì Học Được

- Con đường phát triển sự nghiệp cloud có lộ trình rõ ràng (8 bước), và đóng góp cộng đồng là phần thiết yếu chứ không phải hoạt động phụ.
- Bốn nguyên tắc thiết kế hệ thống phân tán (Separation of Concerns, Defense at the Edge, Pre-computation over On-demand, Cache-aside Pattern) có thể áp dụng rộng rãi cho nhiều bài toán khác nhau.
- Kỹ năng kỹ thuật là điều kiện cần nhưng chưa đủ; giao tiếp, văn hóa chuyên nghiệp và tư duy business là yếu tố phân biệt kỹ sư giỏi với kỹ sư có giá trị thực sự trong tổ chức.
- Vai trò Data Analytics Engineer không chỉ viết SQL và tạo dashboard, mà còn thiết kế data pipeline và là cầu nối giữa kỹ thuật và business.

### Ứng Dụng Vào Công Việc

- Áp dụng bốn nguyên tắc thiết kế từ dự án URL Shortener (đặc biệt Cache-aside Pattern và Separation of Concerns) vào thiết kế API serving layer của dự án cuối kỳ CloudBrief.
- Định hướng xây dựng portfolio cá nhân ngay từ trong quá trình thực tập: dự án CloudBrief, các bài blog, chứng chỉ AWS.
- Rèn luyện thêm kỹ năng trình bày và giao tiếp kỹ thuật cho người không chuyên, không chỉ tập trung vào kỹ năng lập trình/triển khai.
- Ghi nhớ nguyên tắc "Share Back" – chủ động chia sẻ lại kiến thức đã học cho cộng đồng sau khi hoàn thành chương trình thực tập.

### Trải nghiệm trong sự kiện

Buổi tham dự **First Cloud AI Journey Community Day** mang lại nhiều giá trị vượt ngoài ba bài thuyết trình: cơ hội networking trực tiếp với cộng đồng AWS Việt Nam, gặp gỡ học viên FCJ đồng khóa và cập nhật xu hướng ngành. Em có cơ hội trao đổi ý tưởng về dự án cuối kỳ CloudBrief và nhận được phản hồi hữu ích từ những người có kinh nghiệm. Nhìn thấy hành trình của người đi trước – từ sinh viên FCJ đến AWS Partner – tạo động lực mạnh mẽ để em hoàn thành tốt dự án cuối kỳ.
