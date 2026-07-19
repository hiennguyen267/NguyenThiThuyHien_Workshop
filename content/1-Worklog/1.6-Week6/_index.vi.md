---
title: "Worklog Tuần 6"
date: 2026-05-25
weight: 6
chapter: false
pre: " <b> 1.6. </b> "
---


### Mục tiêu tuần 6

* Hiểu kiến trúc và các khái niệm về mạng của dịch vụ Amazon Virtual Private Cloud (Amazon VPC).
* Tìm hiểu cách thiết kế và cấu hình một mạng riêng ảo an toàn trên nền tảng AWS.
* Thực hành tạo Subnet, Route Table, Internet Gateway và cấu hình các thành phần bảo mật mạng.
* Hiểu cơ chế giao tiếp giữa các tài nguyên AWS bên trong một Amazon VPC.

### Các công việc thực hiện trong tuần

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Tài liệu tham khảo |
| --- | --------- | ------------ | --------------- | ------------------ |
| 2   | - Tìm hiểu các khái niệm về Amazon VPC.<br>- Nghiên cứu CIDR Block, các thành phần của VPC và kiến thức cơ bản về mạng.<br>- Tìm hiểu kiến trúc mạng AWS và các phương pháp triển khai tốt nhất. | 25/05/2026 | 25/05/2026 |
| 3   | - Tạo một Amazon VPC.<br>- Cấu hình Public Subnet và Private Subnet.<br>- Thiết lập CIDR Block và Availability Zone phù hợp cho từng Subnet. | 26/05/2026 | 26/05/2026 |
| 4   | - Cấu hình Route Tables và Internet Gateway.<br>- Liên kết Route Table với các Subnet tương ứng.<br>- Kiểm tra khả năng kết nối Internet của các tài nguyên trong Public Subnet. | 27/05/2026 | 27/05/2026 |
| 5   | - Cấu hình Security Groups và Network ACLs.<br>- Thiết lập các quy tắc Inbound và Outbound.<br>- So sánh chức năng của Security Groups và Network ACLs. | 28/05/2026 | 28/05/2026 |
| 6   | - Kiểm tra kết nối giữa các tài nguyên trong Amazon VPC.<br>- Xác minh cấu hình mạng và xử lý các lỗi kết nối.<br>- Tổng hợp kiến thức và hoàn thành báo cáo thực tập tuần. | 29/05/2026 | 29/05/2026 |

### Kết quả đạt được tuần 6

* Hiểu toàn diện về dịch vụ **Amazon Virtual Private Cloud (Amazon VPC)**.

* Nắm được các thành phần mạng cốt lõi của Amazon VPC, bao gồm:

  * Virtual Private Cloud (VPC)
  * CIDR Block
  * Public Subnet
  * Private Subnet
  * Route Table
  * Internet Gateway (IGW)
  * NAT Gateway
  * Security Group
  * Network Access Control List (Network ACL)

* Tạo và cấu hình thành công một **Amazon VPC** bao gồm **Public Subnet** và **Private Subnet**.

* Hiểu cách lập kế hoạch địa chỉ IP và phân chia Subnet bằng **CIDR Block**.

* Cấu hình thành công **Route Table** và liên kết với các Subnet phù hợp.

* Thiết lập **Internet Gateway (IGW)** để cho phép các tài nguyên trong Public Subnet có thể truy cập Internet.

* Hiểu được sự khác biệt giữa **Public Subnet** và **Private Subnet**, cũng như các tình huống triển khai phổ biến của từng loại.

* Cấu hình thành công **Security Groups** và **Network ACLs** để kiểm soát lưu lượng truy cập vào và ra khỏi hệ thống.

* Hiểu rõ sự khác biệt giữa:

  * **Security Groups** (Tường lửa có trạng thái - Stateful Firewall)
  * **Network ACLs** (Tường lửa không trạng thái - Stateless Firewall)

* Thực hành kiểm tra kết nối mạng bằng các công cụ mạng thông dụng và xác minh khả năng giao tiếp giữa các tài nguyên AWS trong cùng VPC.

* Nắm được các phương pháp bảo mật mạng theo khuyến nghị của AWS, bao gồm:

  * Cô lập tài nguyên bằng Private Subnet
  * Hạn chế các kết nối Inbound không cần thiết
  * Áp dụng nguyên tắc **Least Privilege**
  * Xây dựng nhiều lớp bảo mật cho hệ thống mạng

* Có kinh nghiệm thực tế trong việc thiết kế kiến trúc mạng Cloud an toàn, linh hoạt và có khả năng mở rộng.

* Nâng cao kỹ năng xử lý sự cố thông qua việc phát hiện và khắc phục các lỗi liên quan đến Route Table, Subnet, Internet Gateway và kết nối mạng trong Amazon VPC.

* Hoàn thiện tài liệu hướng dẫn triển khai Amazon VPC và lưu lại toàn bộ cấu hình mạng để phục vụ việc tham khảo và bảo trì sau này.

* Xây dựng nền tảng vững chắc để triển khai các ứng dụng Cloud có tính sẵn sàng cao, an toàn và khả năng mở rộng, đồng thời chuẩn bị cho việc triển khai dự án **PharmaCare AI** trong các tuần tiếp theo.