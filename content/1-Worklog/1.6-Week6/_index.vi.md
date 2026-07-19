---
title: "Worklog Tuần 6"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 1.6. </b> "
---

**Họ và tên:** Đinh Tuấn Minh &emsp; | &emsp; **MSSV:** 2280601918

**Người hướng dẫn tại đơn vị thực tập:** Nguyễn Gia Hưng – Head of Solution Architect &emsp; | &emsp; **Giảng viên hướng dẫn:** Võ Phạm Thành Luân

**Chủ đề:** Dịch vụ Cơ sở dữ liệu trên AWS

### Mục tiêu tuần 6:

* Hệ thống hóa các khái niệm nền tảng về cơ sở dữ liệu: Relational (SQL) vs Non-Relational (NoSQL), ACID vs BASE, OLTP vs OLAP.
* Nắm vững Amazon RDS: kiến trúc, Multi-AZ Deployment, Read Replica, backup/Point-in-Time Recovery và bảo mật.
* Hiểu sâu Amazon Aurora: kiến trúc storage phân tán 6-way replication, Aurora Cluster, Aurora Serverless v2 và Aurora Global Database.
* Nắm được Amazon Redshift cho data warehouse/OLAP và Amazon ElastiCache cho caching; thực hành triển khai kiến trúc 3-tier với RDS và di chuyển database bằng AWS DMS.

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc                                                                                                                                                                                                                    | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu                            |
| --- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ----------------------------------------- |
| 2   | - Ôn tập khái niệm cơ sở dữ liệu: Relational (SQL) vs Non-Relational (NoSQL), ACID vs BASE, OLTP vs OLAP, các mô hình triển khai (self-managed, managed, serverless) <br> - Amazon RDS: DB Instance, DB Subnet Group, Parameter/Option Group, Multi-AZ Deployment, Read Replica, backup/PITR, encryption và network isolation | 25/05/2026   | 25/05/2026      | <https://cloudjourney.awsstudygroup.com/> |
| 3   | - Amazon Aurora: kiến trúc storage phân tán (6 bản sao/3 AZ), Aurora Cluster (Primary/Replica/Endpoint), Aurora Serverless v2, Aurora Global Database cho multi-region | 26/05/2026   | 26/05/2026      | <https://cloudjourney.awsstudygroup.com/> |
| 4   | - Amazon Redshift: kiến trúc Leader/Compute Node, Columnar Storage, Redshift Spectrum, Redshift Serverless <br> - Amazon ElastiCache: Redis (Multi-AZ, Cluster Mode, persistence) và Memcached; caching patterns (Lazy Loading, Write-Through, TTL) | 27/05/2026   | 27/05/2026      | <https://cloudjourney.awsstudygroup.com/> |
| 5   | - **Thực hành (Lab: Triển khai Amazon RDS và kết nối ứng dụng):** <br>&emsp; + Tạo VPC 3-tier (public subnet cho EC2, private subnet cho RDS) <br>&emsp; + Tạo Security Group riêng cho EC2 và RDS, DB Subnet Group <br>&emsp; + Tạo RDS MySQL instance, deploy ứng dụng kết nối database <br>&emsp; + Thực hành backup thủ công và restore từ snapshot | 28/05/2026   | 28/05/2026      | <https://cloudjourney.awsstudygroup.com/> |
| 6   | - **Thực hành (Lab: AWS Database Migration Service – Di chuyển cơ sở dữ liệu):** <br>&emsp; + Cấu hình SQL Server/Oracle làm source database, dùng AWS SCT chuyển đổi schema <br>&emsp; + Tạo Replication Instance, Endpoint và Migration Task (Full Load + CDC) sang Aurora MySQL/MySQL <br>&emsp; + Tạo DMS Serverless Replication và Event Notification qua SNS <br>&emsp; + Troubleshoot memory pressure và table error trong quá trình migration <br> - Tổng hợp kiến thức, viết báo cáo tuần 6 | 29/05/2026   | 29/05/2026      | <https://cloudjourney.awsstudygroup.com/> |
| 7   | - Tham dự sự kiện **First Cloud AI Journey – Workshop & Community Day** tại AWS Office, tòa nhà Bitexco, TP. Hồ Chí Minh: 6 phần trình bày (AWS Cloud Quest, giới thiệu Hackathon, Why We Always Need Confidence, Tử vi Đại Việt, DevOps Before Disaster, The Iceberg of Procrastination) <br> - Networking với cộng đồng học viên FCAJ | 30/05/2026   | 30/05/2026      | Sự kiện First Cloud AI Journey – Workshop & Community Day |

### Kết quả đạt được tuần 6:

* Hệ thống hóa các khái niệm database nền tảng: SQL vs NoSQL, OLTP vs OLAP, ACID vs BASE, tạo cơ sở để lựa chọn đúng database service cho từng use case.
* Nắm vững Amazon RDS: kiến trúc, Multi-AZ HA, Read Replica scale-out, backup/PITR, encryption và security best practice (private subnet, Security Group isolation).
* Hiểu sâu Amazon Aurora: kiến trúc storage 6-way replication đặc biệt, Aurora Cluster endpoints, Aurora Serverless v2 và Aurora Global Database cho multi-region.
* Phân biệt được khi nào dùng RDS và khi nào dùng Aurora: Aurora phù hợp với workload lớn cần hiệu năng cao và availability tối đa; RDS phù hợp hơn khi cần tương thích engine cụ thể hoặc workload nhỏ hơn.
* Nắm được Amazon Redshift như giải pháp data warehouse MPP cho OLAP, phân biệt rõ vai trò khác nhau của Redshift (analytics) và RDS/Aurora (transactional).
* Hiểu Amazon ElastiCache Redis và Memcached: caching patterns, phân biệt use case của Redis (rich data structure, persistence) và Memcached (simple caching, multi-thread).
* Thực hành triển khai kiến trúc 3-tier với RDS trong private subnet – kiến trúc nền tảng của mọi ứng dụng web production trên AWS.
* Thực hành toàn bộ quy trình database migration với DMS + SCT: heterogeneous migration, CDC replication, DMS Serverless, event notification và troubleshoot lỗi thực tế.
* Tham dự sự kiện cộng đồng First Cloud AI Journey – Workshop & Community Day, học hỏi thêm về kỹ năng mềm (sự tự tin, vượt trì hoãn), DevOps và một case study thực tế về cân nhắc chi phí khi đưa sản phẩm lên AWS.

### Khó khăn và cách khắc phục:

| Khó khăn gặp phải | Cách khắc phục |
| --- | --- |
| Khó xác định khi nào nên dùng RDS và khi nào nên dùng Aurora cho một dự án cụ thể. | So sánh theo tiêu chí hiệu năng, mức độ tương thích engine (Oracle/MSSQL) và chi phí để đưa ra lựa chọn phù hợp. |
| Cấu hình CDC (Change Data Capture) trong migration heterogeneous (Oracle → MySQL) có nhiều bước dễ sai. | Làm theo checklist tuần tự của AWS SCT: cấu hình Supplemental Logging, tạo DMS user đúng quyền, review schema conversion report trước khi apply. |
| Distribution Style và Sort Key của Redshift ảnh hưởng hiệu năng nhưng khó hình dung khi mới học. | Dùng EXPLAIN plan để quan sát thực tế cách query được thực thi và điều chỉnh Sort Key phù hợp. |

### Bài học kinh nghiệm:

* Việc tạo Security Group riêng biệt cho EC2 và RDS rồi chỉ allow traffic từ EC2-SG vào RDS-SG là pattern bảo mật quan trọng, đảm bảo database không bao giờ expose trực tiếp ra internet.
* Kinh nghiệm backup/restore thực tế giúp sẵn sàng cho kịch bản disaster recovery, không chỉ tạo snapshot mà còn phải xác nhận restore hoạt động đúng.
* AWS DMS + SCT bao quát toàn bộ vòng đời của một dự án database migration thực tế: từ chuẩn bị source database, chuyển đổi schema, migration có CDC, đến theo dõi tiến trình và xử lý lỗi.
* Kinh nghiệm troubleshoot memory pressure và table error trong DMS giúp chuẩn bị sẵn sàng cho các vấn đề thường gặp trong môi trường production.

### Kế hoạch tuần tiếp theo:

* Chuyển sang chủ đề Dịch vụ Phân tích Dữ liệu và NoSQL trên AWS: kiến trúc Data Lake và vòng đời dữ liệu (Ingest → Store → Catalog → Transform → Analyze → Visualize → Serve).
* Nắm vững Amazon DynamoDB từ cơ bản đến nâng cao: data model, throughput mode, Secondary Index, Streams, Transactions, DAX, Global Tables và các design pattern.
* Tìm hiểu hệ sinh thái Kinesis (Data Streams, Firehose, Data Analytics), AWS Glue (Data Catalog, ETL Jobs, DataBrew) và Amazon EMR.
* Tìm hiểu Amazon Athena và Amazon QuickSight; thực hành 7 lab xây dựng pipeline phân tích dữ liệu end-to-end.
