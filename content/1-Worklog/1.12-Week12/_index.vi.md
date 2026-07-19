---
title: "Worklog Tuần 12"
date: 2026-07-06
weight: 12
chapter: false
pre: " <b> 1.12. </b> "
---


### Mục tiêu tuần 12

* Hoàn thiện các chức năng còn lại của dự án **PharmaCare AI**.
* Xây dựng chatbot tra cứu thông tin dược phẩm theo mô hình Retrieval-Augmented Generation (RAG).
* Tích hợp chatbot vào React frontend.
* Triển khai frontend bằng Amazon S3 và Amazon CloudFront.
* Thiết lập các cơ chế giám sát, cảnh báo, sao lưu và bảo mật cơ bản.
* Kiểm thử các luồng chức năng chính và khả năng kết nối giữa các dịch vụ.
* Tổng hợp ảnh minh chứng và hoàn thiện tài liệu thực tập.

### Các công việc thực hiện trong tuần

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Tài liệu tham khảo |
| --- | --------- | ------------ | --------------- | ------------------ |
| 2   | - Tạo S3 bucket private để lưu hình ảnh sản phẩm.<br>- Tải hình ảnh lên prefix products/, tạo CloudFront Distribution và cập nhật URL hình ảnh vào RDS bằng Lambda migration. | 06/07/2026 | 06/07/2026 |
| 3   | - Tạo S3 bucket lưu kho tri thức.<br>- Tổ chức tài liệu theo nhóm FAQ, sản phẩm, bài viết sức khỏe, hướng dẫn y tế và an toàn.<br>- Cấu hình Bedrock, OpenSearch Serverless, IAM Role và VPC Endpoint. | 07/07/2026 | 07/07/2026 |
| 4   | - Xây dựng Lambda pharmacare-rag-indexing.<br>- Đọc tài liệu từ S3, chia nội dung thành chunk, tạo embedding bằng Cohere Embed Multilingual và ghi vector vào OpenSearch Serverless. | 08/07/2026 | 08/07/2026 |
| 5   | - Xây dựng Lambda pharmacare-rag-chatbot.<br>- Tạo vector cho câu hỏi, truy vấn ba nội dung liên quan nhất và trả kết quả kèm nguồn tham khảo.<br>- Tích hợp chatbot vào React frontend. | 09/07/2026 | 09/07/2026 |
| 6   | - Build React frontend và triển khai lên S3, CloudFront.<br>- Cấu hình Cognito callback URL, CloudWatch Logs, CloudWatch Alarm, SNS Topic, AWS Backup và AWS WAF.<br>- Kiểm thử hệ thống và tổng hợp ảnh minh chứng. | 10/07/2026 | 10/07/2026 |

### Kết quả đạt được tuần 12

* Hoàn thành việc lưu trữ hình ảnh sản phẩm trong Amazon S3.

* Giữ S3 bucket ở trạng thái private và phân phối hình ảnh thông qua Amazon CloudFront.

* Cập nhật đường dẫn CloudFront vào dữ liệu sản phẩm trong Amazon RDS bằng Lambda migration.

* Tạo kho tri thức cho chatbot trên Amazon S3 và tổ chức tài liệu theo các nhóm nội dung:

  * Câu hỏi thường gặp.
  * Thông tin sản phẩm.
  * Bài viết sức khỏe.
  * Hướng dẫn sử dụng.
  * Nội dung an toàn liên quan đến dược phẩm.

* Cấu hình mô hình **Cohere Embed Multilingual** trên Amazon Bedrock để tạo vector embedding cho tài liệu và câu hỏi tiếng Việt.

* Tạo Amazon OpenSearch Serverless Collection loại Vector Search để lưu trữ và truy vấn dữ liệu vector.

* Cấu hình OpenSearch Serverless hoạt động trong mạng private thông qua VPC Endpoint.

* Tạo IAM Role dành riêng cho các Lambda của hệ thống RAG và cấp các quyền cần thiết để:

  * Đọc tài liệu từ Amazon S3.
  * Gọi mô hình embedding trên Amazon Bedrock.
  * Ghi và truy vấn dữ liệu trong OpenSearch Serverless.
  * Ghi nhật ký thực thi vào Amazon CloudWatch Logs.

* Xây dựng Lambda `pharmacare-rag-indexing` để thực hiện quy trình:

  * Đọc tài liệu từ Amazon S3.
  * Chuẩn hóa nội dung.
  * Chia tài liệu thành các chunk.
  * Tạo vector embedding.
  * Lưu vector, nội dung và metadata vào OpenSearch Serverless.

* Kiểm thử Lambda Indexing và đạt được kết quả:

  * Xử lý thành công 250 tài liệu.
  * Tạo 1.186 chunk.
  * Ghi dữ liệu thành công vào OpenSearch Serverless Vector Store.

* Xây dựng Lambda `pharmacare-rag-chatbot` để:

  * Tiếp nhận câu hỏi của người dùng.
  * Kiểm tra dữ liệu đầu vào.
  * Tạo vector embedding cho câu hỏi.
  * Truy vấn ba đoạn tài liệu có nội dung liên quan nhất.
  * Trả kết quả kèm theo nguồn tài liệu tham khảo.

* Cấu hình chatbot hoạt động chủ yếu ở chế độ RAG-only với `ENABLE_LLM=false` trong giai đoạn kiểm thử nhằm giảm mức sử dụng token và chi phí.

* Chuẩn bị khả năng sử dụng Amazon Nova Micro khi chuyển `ENABLE_LLM=true` để tổng hợp câu trả lời tự nhiên từ các nội dung được truy xuất.

* Tích hợp giao diện chatbot vào React frontend và kiểm tra khả năng gửi câu hỏi, nhận kết quả và hiển thị nguồn tham khảo.

* Build React frontend bằng Vite và tạo bản triển khai production trong thư mục `dist`.

* Tải các tệp frontend lên S3 bucket private và phân phối website bằng Amazon CloudFront qua giao thức HTTPS.

* Cấu hình CloudFront Custom Error Response cho mã lỗi `403` và `404` để hỗ trợ cơ chế định tuyến của React Router.

* Cập nhật callback URL và sign-out URL trong Amazon Cognito để hỗ trợ quá trình đăng nhập và đăng xuất trên frontend đã triển khai.

* Thiết lập Amazon CloudWatch Logs cho các Lambda function:

  * `pharmacare-backend-api`.
  * `pharmacare-db-migration`.
  * `pharmacare-rag-indexing`.
  * `pharmacare-rag-chatbot`.

* Tạo CloudWatch Alarm để theo dõi:

  * Mức sử dụng CPU của Amazon RDS.
  * Lỗi 5xx của API.
  * Lỗi thực thi Lambda backend.
  * Lỗi thực thi Lambda chatbot.

* Tạo SNS Topic `pharmacare-alert-topic` phục vụ gửi cảnh báo đến quản trị viên.

* Tạo AWS Backup Plan cho Amazon RDS với lịch sao lưu hằng ngày.

* Bật AWS WAF Core Protections cho CloudFront nhằm hỗ trợ phát hiện và hạn chế các yêu cầu web bất thường.

* Rà soát IAM Role và IAM Policy của backend Lambda và Lambda AI theo nguyên tắc **Least Privilege**.

* Thực hiện kiểm thử các luồng chức năng chính của hệ thống, bao gồm:

  * Đăng ký và đăng nhập bằng Amazon Cognito.
  * Truy cập public API.
  * Truy cập protected API bằng JWT.
  * Xem danh sách và chi tiết sản phẩm.
  * Quản lý hồ sơ người dùng.
  * Quản lý giỏ hàng.
  * Tạo và xem đơn hàng.
  * Hiển thị hình ảnh sản phẩm qua CloudFront.
  * Đặt câu hỏi và nhận kết quả từ chatbot RAG.

* Xác nhận khả năng giao tiếp giữa các thành phần chính:

  * React frontend → Amazon Cognito.
  * React frontend → Amazon API Gateway.
  * Amazon API Gateway → AWS Lambda.
  * AWS Lambda → AWS Secrets Manager.
  * AWS Lambda → Amazon RDS.
  * AWS Lambda → Amazon Bedrock.
  * AWS Lambda → Amazon OpenSearch Serverless.
  * Amazon CloudFront → Amazon S3.

* Tổng hợp ảnh minh chứng và hoàn thiện nội dung workshop hướng dẫn triển khai dự án **PharmaCare AI**.

* Hoàn thành bản demo các chức năng chính của PharmaCare AI trên nền tảng AWS.

### Nội dung chưa hoàn thành và định hướng phát triển

* Chưa hoàn tất việc đăng ký và gắn domain riêng bằng Amazon Route 53.

* Chưa xây dựng quy trình Continuous Integration/Continuous Deployment (CI/CD) để tự động hóa quá trình triển khai.

* Chưa sử dụng Terraform hoặc AWS CloudFormation để quản lý hạ tầng dưới dạng mã nguồn.

* Chưa thực hiện kiểm thử tải với số lượng lớn người dùng đồng thời.

* Chưa thực hiện đầy đủ bài kiểm thử khôi phục Amazon RDS từ recovery point.

* Email subscription của Amazon SNS cần được xác nhận trước khi có thể nhận thông báo.

* Các rule của AWS WAF cần được tiếp tục theo dõi ở chế độ Count hoặc Monitor trước khi chuyển sang chế độ Block.

* Chatbot hiện được kiểm thử chủ yếu ở chế độ RAG-only. Việc sử dụng Amazon Nova Micro cần tiếp tục được đánh giá về chất lượng câu trả lời, quota và chi phí.

### Tự đánh giá tuần 12

* Hoàn thành các mục tiêu chính đã đề ra trong tuần.

* Vận dụng được kiến thức về Amazon S3, CloudFront, Lambda, Bedrock, OpenSearch Serverless, CloudWatch, SNS, AWS Backup và AWS WAF vào dự án thực tế.

* Nâng cao khả năng tích hợp nhiều dịch vụ AWS trong cùng một hệ thống.

* Cải thiện kỹ năng xử lý lỗi liên quan đến IAM Policy, Data Access Policy, VPC Endpoint, Security Group và kết nối mạng private.

* Nâng cao kỹ năng kiểm thử, tổng hợp ảnh minh chứng và viết tài liệu kỹ thuật.

* Nhận thấy bản thân cần tiếp tục phát triển kiến thức về Infrastructure as Code, CI/CD, kiểm thử hiệu năng, tối ưu chi phí và vận hành hệ thống trong môi trường production.

* Hoàn thành chương trình thực tập 12 tuần và xây dựng được nền tảng kiến thức phục vụ các định hướng nghề nghiệp như:

  * Cloud Engineer.
  * DevOps Engineer.
  * AWS Solutions Architect.