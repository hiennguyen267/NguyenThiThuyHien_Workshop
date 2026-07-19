---
title: "Worklog Tuần 7"
date: 2026-06-01
weight: 7
chapter: false
pre: " <b> 1.7. </b> "
---



### Mục tiêu tuần 7

* Hiểu các khái niệm và kiến trúc của dịch vụ Elastic Load Balancing (ELB).
* Tìm hiểu cách phân phối lưu lượng truy cập đến nhiều Amazon EC2 Instance.
* Cấu hình Auto Scaling để tự động mở rộng hoặc thu hẹp tài nguyên theo nhu cầu sử dụng.
* Giám sát tài nguyên AWS bằng Amazon CloudWatch và cấu hình cảnh báo để chủ động theo dõi hệ thống.

### Các công việc thực hiện trong tuần

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Tài liệu tham khảo |
| --- | --------- | ------------ | --------------- | ------------------ |
| 2   | - Tìm hiểu các khái niệm về Elastic Load Balancer (ELB).<br>- Phân biệt các loại Load Balancer trên AWS.<br>- Tìm hiểu các trường hợp sử dụng và kiến trúc đảm bảo tính sẵn sàng cao (High Availability). | 01/06/2026 | 01/06/2026 |
| 3   | - Cấu hình Application Load Balancer (ALB).<br>- Tạo Target Groups.<br>- Đăng ký các EC2 Instance và kiểm tra khả năng phân phối lưu lượng truy cập. | 02/06/2026 | 02/06/2026 |
| 4   | - Tạo Auto Scaling Group.<br>- Cấu hình Launch Template.<br>- Thiết lập chính sách Auto Scaling dựa trên mức sử dụng CPU. | 03/06/2026 | 03/06/2026 |
| 5   | - Tìm hiểu dịch vụ Amazon CloudWatch.<br>- Theo dõi các chỉ số hoạt động của EC2.<br>- Tìm hiểu Dashboard, Logs và các tính năng giám sát của CloudWatch. | 04/06/2026 | 04/06/2026 |
| 6   | - Cấu hình CloudWatch Alarm.<br>- Thiết lập cảnh báo khi CPU Utilization vượt ngưỡng.<br>- Ôn tập ELB, Auto Scaling và CloudWatch.<br>- Hoàn thành và nộp báo cáo thực tập tuần. | 05/06/2026 | 05/06/2026 |

### Kết quả đạt được tuần 7

* Hiểu toàn diện về dịch vụ **Elastic Load Balancing (ELB)** và vai trò của dịch vụ này trong việc xây dựng hệ thống có tính sẵn sàng cao trên AWS.

* Nắm được các loại Load Balancer trên AWS, bao gồm:

  * Application Load Balancer (ALB)
  * Network Load Balancer (NLB)
  * Gateway Load Balancer (GWLB)
  * Classic Load Balancer (Tổng quan)

* Cấu hình thành công **Application Load Balancer (ALB)** để phân phối lưu lượng truy cập đến nhiều Amazon EC2 Instance.

* Hiểu cách hoạt động của **Target Groups** và mối quan hệ giữa Target Groups với các EC2 Instance.

* Nắm được các thành phần chính của Elastic Load Balancer, bao gồm:

  * Listener
  * Listener Rules
  * Target Groups
  * Health Checks
  * Routing Policies

* Tạo và cấu hình thành công **Auto Scaling Group**.

* Hiểu cơ chế Auto Scaling giúp tự động tăng hoặc giảm số lượng EC2 Instance dựa trên nhu cầu sử dụng tài nguyên của hệ thống.

* Cấu hình **Launch Template** và các chính sách Auto Scaling nhằm nâng cao hiệu năng và khả năng sẵn sàng của ứng dụng.

* Hiểu toàn diện về dịch vụ **Amazon CloudWatch**, bao gồm:

  * Metrics
  * Dashboards
  * Logs
  * Events
  * Alarms

* Theo dõi thành công hiệu năng của EC2 thông qua các chỉ số quan trọng như:

  * CPU Utilization
  * Network In
  * Network Out
  * Disk Read/Write Operations
  * Status Check Metrics

* Cấu hình **CloudWatch Alarms** để tự động gửi cảnh báo khi mức sử dụng tài nguyên vượt quá ngưỡng đã thiết lập.

* Hiểu mối liên kết giữa các dịch vụ:

  * Elastic Load Balancer
  * Auto Scaling
  * Amazon CloudWatch
  * Amazon EC2

  trong việc xây dựng hệ thống có khả năng mở rộng và giám sát tự động.

* Nắm được các phương pháp triển khai hệ thống theo khuyến nghị của AWS nhằm đảm bảo:

  * Khả năng mở rộng (Scalability)
  * Tính sẵn sàng cao (High Availability)
  * Khả năng chịu lỗi (Fault Tolerance)

* Nâng cao kỹ năng kiểm thử và xử lý sự cố thông qua việc kiểm tra hoạt động của Load Balancer, Auto Scaling và CloudWatch.

* Hoàn thiện tài liệu hướng dẫn triển khai, sơ đồ kiến trúc và cấu hình giám sát hệ thống để phục vụ việc vận hành và bảo trì.

* Xây dựng nền tảng vững chắc để tiếp tục nghiên cứu các dịch vụ **AWS CLI, AWS Lambda** và các công nghệ **Serverless** trong những tuần tiếp theo.