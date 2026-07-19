---
title: "Worklog Tuần 7"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 1.7. </b> "
---

**Họ và tên:** Đinh Tuấn Minh &emsp; | &emsp; **MSSV:** 2280601918

**Người hướng dẫn tại đơn vị thực tập:** Nguyễn Gia Hưng – Head of Solution Architect &emsp; | &emsp; **Giảng viên hướng dẫn:** Võ Phạm Thành Luân

**Chủ đề:** Dịch vụ Phân tích Dữ liệu và NoSQL trên AWS

### Mục tiêu tuần 7:

* Hiểu kiến trúc Data Lake trên AWS và vòng đời dữ liệu: Ingest → Store → Catalog → Transform → Analyze → Visualize → Serve.
* Nắm vững Amazon DynamoDB từ cơ bản đến nâng cao: data model, Secondary Index, Streams, Transactions, DAX, Global Tables và các design pattern.
* Hiểu hệ sinh thái streaming và ETL trên AWS: Amazon Kinesis, AWS Glue và Amazon EMR.
* Nắm vững Amazon Athena cho serverless SQL query và Amazon QuickSight cho trực quan hóa dữ liệu; thực hành xây dựng pipeline phân tích dữ liệu end-to-end.

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc                                                                                                                                                                                                                    | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu                            |
| --- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ----------------------------------------- |
| 2   | - Tổng quan Data Lake trên AWS và vòng đời dữ liệu (Ingest, Store, Catalog, Transform, Analyze, Visualize, Serve) <br> - Amazon DynamoDB: data model (Table/Item/Attribute), Partition Key/Sort Key, Global/Local Secondary Index, throughput mode (Provisioned/On-Demand), Streams, Transactions, DAX, Global Tables, các design pattern | 01/06/2026   | 01/06/2026      | <https://cloudjourney.awsstudygroup.com/> |
| 3   | - Amazon Kinesis: Data Streams, Data Firehose, Data Analytics <br> - AWS Glue: Data Catalog, Crawler, ETL Jobs, DynamicFrame, Interactive Sessions, Workflows, Glue DataBrew <br> - Amazon EMR: kiến trúc cluster, EMR Serverless, EMR on EKS | 02/06/2026   | 02/06/2026      | <https://cloudjourney.awsstudygroup.com/> |
| 4   | - Amazon Athena: serverless SQL query trên S3, Federated Query, Workgroups <br> - Amazon QuickSight: SPICE, Data Sources, Analyses/Dashboards, ML Insights <br> - **Thực hành (Lab: Pipeline phân tích dữ liệu với Kinesis, Glue, Athena và QuickSight):** tạo Firehose Delivery Stream, Glue Crawler, query bằng Athena, trực quan hóa với QuickSight | 03/06/2026   | 03/06/2026      | <https://cloudjourney.awsstudygroup.com/> |
| 5   | - **Thực hành (Lab: DynamoDB từ cơ bản đến nâng cao):** CRUD cơ bản, backup/PITR, Single Table Design, GSI Overloading, Global Tables, DynamoDB Streams + Lambda <br> - **Thực hành (Lab: Redshift – Phân tích chi phí và query nâng cao):** load dữ liệu, Distribution Style, cost allocation tag, EXPLAIN plan <br> - **Thực hành (Lab: Truy cập DynamoDB qua CloudShell, Console và SDK)** <br> - **Thực hành (Lab: AWS Glue DataBrew):** data profiling, làm sạch và chuẩn hóa dữ liệu | 04/06/2026   | 04/06/2026      | <https://cloudjourney.awsstudygroup.com/> |
| 6   | - **Thực hành (Lab: Data Lake End-to-End Pipeline):** ingest/store 3-zone S3, catalog với Lake Formation, transform bằng Glue Interactive/GUI/DataBrew/EMR, analyze với Athena/Kinesis Data Analytics, serve qua Lambda, warehouse trên Redshift <br> - **Thực hành (Lab: Xây dựng Dashboard với Amazon QuickSight):** dashboard cơ bản, conditional formatting, dashboard tương tác với Filter/Action <br> - Tổng hợp kiến thức, viết báo cáo tuần 7 | 05/06/2026   | 05/06/2026      | <https://cloudjourney.awsstudygroup.com/> |

### Kết quả đạt được tuần 7:

* Hiểu kiến trúc Data Lake trên AWS: S3 làm trung tâm, pipeline dữ liệu theo vòng đời Ingest → Store → Catalog → Transform → Analyze → Visualize → Serve.
* Nắm vững Amazon DynamoDB từ cơ bản đến nâng cao: data model, throughput mode, Secondary Index, Streams, Transactions, DAX, Global Tables và các design pattern thực tế.
* Hiểu Amazon Kinesis ecosystem: Data Streams (custom consumer), Firehose (managed delivery), Data Analytics (real-time SQL/Flink).
* Nắm được AWS Glue: Data Catalog và Crawler, Glue ETL, Interactive Sessions, Workflows.
* Thực hành AWS Glue DataBrew cho data preparation visual: profiling, cleaning và transformation không cần code.
* Hiểu Amazon EMR cho big data processing cần tùy biến cao với Apache Spark/Hadoop trên managed cluster.
* Nắm vững Amazon Athena: serverless SQL query trực tiếp trên S3, tối ưu chi phí bằng Parquet và partitioning, Federated Query.
* Thực hành xây dựng dashboard chuyên nghiệp với Amazon QuickSight: từ static visualization đến interactive dashboard với filter và action.
* Hoàn thành 7 lab thực hành, đặc biệt lab Data Lake end-to-end pipeline – lab tổng hợp đa dịch vụ toàn diện nhất.

### Khó khăn và cách khắc phục:

| Khó khăn gặp phải | Cách khắc phục |
| --- | --- |
| Thiết kế schema DynamoDB hoàn toàn khác relational database, khó tư duy access pattern trước khi thiết kế. | Thực hành theo các design pattern cụ thể: Single Table Design, Adjacency List Pattern, Write Sharding và Sparse Index. |
| Nhiều công cụ ETL (Glue ETL, DataBrew, EMR) dễ nhầm lẫn khi nào nên dùng công cụ nào. | So sánh theo tiêu chí: Glue ETL (batch, code-first), DataBrew (no-code, data quality), EMR (large-scale, custom framework), Athena (ad-hoc query). |
| Pipeline Lab Data Lake end-to-end có nhiều bước và nhiều dịch vụ, dễ lạc hướng khi thực hành. | Làm theo checklist tuần tự: Ingest → Store → Catalog → Transform → Analyze → Serve → Visualize, kiểm tra kết quả từng bước trước khi qua bước kế tiếp. |

### Bài học kinh nghiệm:

* Kiến trúc S3 → Firehose → Glue Crawler → Athena → QuickSight là pattern phổ biến nhất cho analytics use case, chi phí thấp do serverless và không cần quản lý infrastructure.
* Nguyên tắc quan trọng nhất khi thiết kế DynamoDB là "biết access pattern trước khi thiết kế schema" – hoàn toàn khác tư duy relational database.
* Tag-based cost allocation là best practice quan trọng để phân bổ chi phí cloud chính xác cho từng team/project, đặc biệt với Redshift.
* AWS Glue DataBrew giải quyết một trong những bottleneck lớn nhất trong data project: phần lớn thời gian thường dành cho data cleaning; Data Profile report giúp tránh "garbage in, garbage out".
* Không có một công cụ duy nhất phù hợp cho mọi bài toán phân tích dữ liệu – lựa chọn đúng công cụ cho đúng bài toán là kỹ năng quan trọng của Data Engineer.
* Dashboard tương tác trong QuickSight giúp người dùng tự khám phá dữ liệu theo nhu cầu, giảm phụ thuộc vào data team cho mỗi yêu cầu báo cáo.

### Kế hoạch tuần tiếp theo:

* Đề xuất và trình bày dự án cuối kỳ của nhóm dựa trên nền tảng kiến thức Compute, Storage, Security, Database và Analytics đã học qua 7 tuần.
* Viết và đăng một bài blog chia sẻ kiến thức lên cộng đồng AWS Study Group VN.
* Tham dự sự kiện cộng đồng do First Cloud AI Journey tổ chức để giao lưu, học hỏi kinh nghiệm thực tế và mở rộng mạng lưới quan hệ.
