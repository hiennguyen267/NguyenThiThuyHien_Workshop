---
title: "Worklog Tuần 8"
date: 2026-06-08
weight: 8
chapter: false
pre: " <b> 1.8. </b> "
---

### Mục tiêu tuần 8

* Hiểu các kiến thức nền tảng về AWS Command Line Interface (AWS CLI) và mô hình điện toán không máy chủ (Serverless Computing).
* Tìm hiểu cách cấu hình và quản lý tài nguyên AWS bằng AWS CLI.
* Thực hành quản lý Amazon EC2 và Amazon S3 thông qua các lệnh trên giao diện dòng lệnh.
* Hiểu các khái niệm, kiến trúc và trường hợp sử dụng của AWS Lambda.

### Các công việc thực hiện trong tuần

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Tài liệu tham khảo |
| --- | --------- | ------------ | --------------- | ------------------ |
| 2   | - Cài đặt AWS Command Line Interface (AWS CLI).<br>- Kiểm tra quá trình cài đặt.<br>- Tìm hiểu cú pháp và các lệnh AWS CLI thường dùng. | 08/06/2026 | 08/06/2026 |
| 3   | - Cấu hình AWS CLI bằng Access Key ID và Secret Access Key.<br>- Thiết lập Region mặc định và định dạng đầu ra (Output Format).<br>- Kiểm tra cấu hình AWS CLI. | 09/06/2026 | 09/06/2026 |
| 4   | - Quản lý Amazon EC2 và Amazon S3 bằng AWS CLI.<br>- Xem thông tin các EC2 Instance.<br>- Tạo và quản lý Bucket cũng như Object trên Amazon S3 bằng các lệnh CLI. | 10/06/2026 | 10/06/2026 |
| 5   | - Tìm hiểu kiến trúc AWS Lambda.<br>- Nghiên cứu mô hình Serverless Computing.<br>- Tạo và kiểm thử một hàm AWS Lambda đơn giản. | 11/06/2026 | 11/06/2026 |
| 6   | - So sánh Amazon EC2 và AWS Lambda.<br>- Xác định các trường hợp sử dụng phù hợp của từng dịch vụ.<br>- Ôn tập các bài thực hành và hoàn thành báo cáo thực tập tuần. | 12/06/2026 | 12/06/2026 |

### Kết quả đạt được tuần 8

* Hiểu toàn diện về **AWS Command Line Interface (AWS CLI)**.

* Cài đặt và cấu hình thành công **AWS CLI** trên máy tính cá nhân.

* Nắm được các thông số cấu hình quan trọng của AWS CLI, bao gồm:

  * Access Key ID
  * Secret Access Key
  * Default Region
  * Output Format

* Thực hành quản lý các tài nguyên AWS thông qua AWS CLI, bao gồm:

  * Xem danh sách EC2 Instance
  * Khởi động và dừng EC2 Instance
  * Liệt kê các Amazon S3 Bucket
  * Tải lên và tải xuống Object
  * Quản lý Bucket và tệp trên Amazon S3

* Hiểu những lợi ích của việc quản lý hạ tầng bằng giao diện dòng lệnh, giúp tự động hóa các tác vụ quản trị trên AWS.

* Hiểu rõ mô hình **Serverless Computing** và các ưu điểm của mô hình này, bao gồm:

  * Không cần quản lý máy chủ
  * Tự động mở rộng theo lưu lượng truy cập
  * Thực thi theo sự kiện (Event-driven)
  * Thanh toán theo mức sử dụng (Pay-per-use)

* Nắm được kiến trúc và quy trình hoạt động của **AWS Lambda**, bao gồm:

  * Lambda Function
  * Trigger
  * Event
  * Execution Environment
  * Runtime Environment

* Tạo và kiểm thử thành công một **AWS Lambda Function** cơ bản.

* Hiểu cách AWS Lambda tích hợp với các dịch vụ AWS khác như:

  * Amazon S3
  * Amazon API Gateway
  * Amazon CloudWatch
  * Amazon DynamoDB
  * Amazon EventBridge

* So sánh Amazon EC2 và AWS Lambda dựa trên các tiêu chí:

  * Quản lý hạ tầng
  * Khả năng mở rộng
  * Mô hình tính phí
  * Thời gian khởi động
  * Thời gian thực thi
  * Trường hợp sử dụng phù hợp

* Biết cách lựa chọn giữa **Amazon EC2** và **AWS Lambda** tùy theo yêu cầu của ứng dụng và bài toán nghiệp vụ.

* Nâng cao kỹ năng tự động hóa bằng cách quản lý tài nguyên AWS thông qua **AWS CLI** thay vì chỉ sử dụng AWS Management Console.

* Hoàn thiện tài liệu hướng dẫn sử dụng AWS CLI, các bài thực hành AWS Lambda và bảng so sánh EC2 với Lambda để phục vụ việc tham khảo sau này.

* Xây dựng nền tảng vững chắc để áp dụng các công nghệ **AWS CLI**, **Serverless Computing** và **AWS Lambda** vào quá trình triển khai dự án **PharmaCare AI** trong các tuần tiếp theo.