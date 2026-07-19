---
title: "Worklog Tuần 3"
date: 2026-05-04
weight: 3
chapter: false
pre: " <b> 1.3. </b> "
---



### Mục tiêu tuần 3

* Hiểu các kiến thức nền tảng về dịch vụ Amazon Elastic Compute Cloud (Amazon EC2).
* Tìm hiểu cách khởi tạo, cấu hình và quản lý máy chủ EC2 trên AWS.
* Thực hành kết nối đến EC2 thông qua SSH và làm quen với các thao tác quản trị Linux cơ bản.

### Các công việc thực hiện trong tuần

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Tài liệu tham khảo |
| --- | --------- | ------------ | --------------- | ------------------ |
| 2   | - Tìm hiểu các khái niệm về Amazon EC2 và các loại Instance Types.<br>- Nghiên cứu Amazon Machine Image (AMI), Instance Types và các mô hình tính phí của EC2.<br>- Tìm hiểu các trường hợp sử dụng và mô hình triển khai EC2 phổ biến. | 04/05/2026 | 04/05/2026 |
| 3   | - Khởi tạo một Amazon Linux EC2 Instance.<br>- Lựa chọn AMI và Instance Type phù hợp.<br>- Cấu hình lưu trữ (Storage) và thiết lập mạng (Networking) khi tạo EC2 Instance. | 05/05/2026 | 05/05/2026 |
| 4   | - Tạo và cấu hình Key Pair.<br>- Thiết lập Security Groups để cho phép kết nối SSH.<br>- Kiểm tra các quy tắc Inbound và Outbound của Security Group. | 06/05/2026 | 06/05/2026 |
| 5   | - Kết nối đến EC2 thông qua SSH.<br>- Thực hành các lệnh Linux cơ bản.<br>- Quản lý tệp, thư mục và phân quyền người dùng trên Amazon Linux. | 07/05/2026 | 07/05/2026 |
| 6   | - Tìm hiểu về Elastic IP.<br>- Gán Elastic IP cho EC2 Instance.<br>- Ôn tập quá trình triển khai EC2 và hoàn thành báo cáo tuần. | 08/05/2026 | 08/05/2026 |

### Kết quả đạt được tuần 3

* Hiểu toàn diện về dịch vụ **Amazon Elastic Compute Cloud (Amazon EC2)**.

* Nắm được các thành phần cốt lõi của Amazon EC2, bao gồm:

  * Amazon Machine Image (AMI)
  * Instance Types
  * Key Pair
  * Security Group
  * Elastic IP Address
  * Amazon Elastic Block Store (Amazon EBS)

* Khởi tạo và cấu hình thành công một **Amazon Linux EC2 Instance**.

* Hiểu được vòng đời của một EC2 Instance, bao gồm:

  * Launch (Khởi tạo)
  * Start (Khởi động)
  * Stop (Dừng)
  * Reboot (Khởi động lại)
  * Terminate (Xóa)

* Cấu hình thành công Key Pair và kết nối đến EC2 Instance thông qua giao thức SSH từ máy tính cá nhân.

* Thiết lập Security Groups để cho phép truy cập SSH một cách an toàn theo các khuyến nghị bảo mật của AWS.

* Thực hành các thao tác quản trị Linux cơ bản trên Amazon Linux, bao gồm:

  * Quản lý tệp và thư mục
  * Quản lý người dùng và phân quyền
  * Theo dõi tiến trình hệ thống
  * Cài đặt và cập nhật các gói phần mềm
  * Sử dụng các lệnh mạng cơ bản

* Hiểu cách cấp phát, gán và thu hồi Elastic IP cho EC2 Instance.

* Hiểu mối quan hệ giữa các dịch vụ:

  * Amazon EC2
  * Amazon VPC
  * Security Groups
  * Elastic IP

  trong quá trình triển khai hạ tầng trên nền tảng AWS.

* Có kinh nghiệm thực tế trong việc triển khai và quản lý máy chủ ảo trên nền tảng AWS.

* Nâng cao kỹ năng xử lý sự cố bằng cách xác định và khắc phục các lỗi phổ biến liên quan đến kết nối SSH và cấu hình bảo mật.

* Hoàn thiện tài liệu hướng dẫn triển khai EC2 và lưu lại kết quả các bài thực hành để phục vụ việc tham khảo sau này.

* Xây dựng nền tảng vững chắc cho việc triển khai các ứng dụng trên nền tảng Cloud và chuẩn bị cho các dịch vụ tiếp theo như Amazon S3, Amazon RDS và Amazon VPC.