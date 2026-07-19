---
title: "Worklog Tuần 11"
date: 2026-06-29
weight: 11
chapter: false
pre: " <b> 1.11. </b> "
---



### Mục tiêu tuần 11

* Rà soát yêu cầu kỹ thuật và kiến trúc của dự án **PharmaCare AI**.
* Đánh giá phương án triển khai ứng dụng bằng Amazon EC2 và so sánh với kiến trúc serverless sử dụng AWS Lambda.
* Điều chỉnh backend từ mô hình máy chủ truyền thống sang kiến trúc serverless.
* Xây dựng hạ tầng mạng và cơ sở dữ liệu cho hệ thống.
* Xây dựng backend API và cơ chế xác thực người dùng.
* Kiểm thử khả năng kết nối giữa frontend và các dịch vụ AWS.

### Các công việc thực hiện trong tuần

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Tài liệu tham khảo |
| --- | --------- | ------------ | --------------- | ------------------ |
| 2   | - Rà soát yêu cầu và kiến trúc dự án **PharmaCare AI**.<br>- Phân tích phương án triển khai ứng dụng bằng Amazon EC2.<br>- Xác định các yêu cầu về mạng, bảo mật và vận hành hệ thống. | 29/06/2026 | 29/06/2026 |
| 3   | - So sánh phương án EC2 với AWS Lambda.<br>- Điều chỉnh backend sang mô hình serverless.<br>- Tạo VPC, Public Subnet, Private App Subnet, Private DB Subnet, Route Table và Security Group. | 30/06/2026 | 30/06/2026 |
| 4   | - Triển khai Amazon RDS for PostgreSQL trong Private DB Subnet.<br>- Lưu thông tin xác thực bằng AWS Secrets Manager.<br>- Tạo Lambda pharmacare-db-migration để khởi tạo cấu trúc dữ liệu. | 01/07/2026 | 01/07/2026 |
| 5   | - Tạo Amazon Cognito User Pool, App Client và hai nhóm Admin, Customer.<br>- Xây dựng Lambda pharmacare-backend-api để xử lý sản phẩm, hồ sơ, giỏ hàng và đơn hàng.| 02/07/2026 | 02/07/2026 |
| 6   | - Tạo API Gateway HTTP API, cấu hình CORS và Cognito JWT Authorizer.<br>- Tạo React frontend bằng Vite để kiểm thử đăng nhập, public API và protected API.<br>- Tổng hợp kết quả tuần.| 03/07/2026 | 03/07/2026 |

### Kết quả đạt được tuần 11

* Rà soát và điều chỉnh kiến trúc tổng thể của dự án **PharmaCare AI**.

* Phân tích phương án sử dụng Amazon EC2 và đánh giá các yêu cầu vận hành của mô hình máy chủ, bao gồm:

  * Cấu hình hệ điều hành.
  * Cài đặt môi trường thực thi.
  * Quản lý bản vá và thư viện phụ thuộc.
  * Theo dõi trạng thái máy chủ.
  * Duy trì tài nguyên hoạt động liên tục.

* So sánh phương án Amazon EC2 với AWS Lambda dựa trên các tiêu chí:

  * Khả năng mở rộng.
  * Công việc quản trị hạ tầng.
  * Chi phí vận hành.
  * Thời gian triển khai.
  * Mức độ phù hợp với phạm vi dự án.

* Lựa chọn kiến trúc serverless cho phần backend của hệ thống nhằm giảm công việc quản trị máy chủ và hỗ trợ mở rộng theo số lượng yêu cầu.

* Xây dựng hạ tầng mạng cho PharmaCare AI, bao gồm:

  * Amazon VPC.
  * Public Subnet.
  * Private App Subnet.
  * Private DB Subnet.
  * Route Table.
  * Internet Gateway.
  * Security Group.

* Phân tách tầng ứng dụng và tầng cơ sở dữ liệu vào các private subnet nhằm hạn chế khả năng truy cập trực tiếp từ Internet.

* Triển khai thành công Amazon RDS for PostgreSQL trong Private DB Subnet.

* Thiết lập Security Group để chỉ cho phép các tài nguyên backend được cấp quyền kết nối đến Amazon RDS qua cổng PostgreSQL `5432`.

* Sử dụng AWS Secrets Manager để mã hóa và lưu trữ thông tin đăng nhập cơ sở dữ liệu, tránh ghi trực tiếp tài khoản hoặc mật khẩu trong mã nguồn.

* Tạo và cấu hình Lambda `pharmacare-db-migration` để:

  * Đọc thông tin kết nối từ AWS Secrets Manager.
  * Kết nối đến Amazon RDS PostgreSQL.
  * Thực thi các câu lệnh migration.
  * Khởi tạo cấu trúc bảng dữ liệu cho hệ thống.

* Tạo Amazon Cognito User Pool và App Client để quản lý quá trình đăng ký, đăng nhập và xác thực người dùng.

* Tạo hai nhóm người dùng:

  * Admin.
  * Customer.

* Xây dựng Lambda `pharmacare-backend-api` bằng Node.js để xử lý các nhóm chức năng:

  * Sản phẩm.
  * Danh mục.
  * Cửa hàng.
  * Hồ sơ người dùng.
  * Giỏ hàng.
  * Đơn hàng.

* Tạo Amazon API Gateway HTTP API và tích hợp với Lambda backend.

* Khai báo các public API cho phép người dùng truy cập mà không cần đăng nhập, bao gồm:

  * Kiểm tra trạng thái backend.
  * Xem danh sách sản phẩm.
  * Xem chi tiết sản phẩm.
  * Xem danh mục.
  * Xem danh sách cửa hàng.

* Khai báo các protected API yêu cầu người dùng đăng nhập, bao gồm:

  * Xem hồ sơ cá nhân.
  * Quản lý giỏ hàng.
  * Tạo đơn hàng.
  * Xem lịch sử đơn hàng.

* Cấu hình Cognito JWT Authorizer để API Gateway kiểm tra token trước khi chuyển yêu cầu đến Lambda.

* Cấu hình CORS để React frontend có thể gửi yêu cầu đến API Gateway.

* Tạo ứng dụng ReactJS bằng Vite để kiểm thử luồng hoạt động:

  * Người dùng đăng nhập bằng Amazon Cognito.
  * Cognito cấp JWT cho frontend.
  * Frontend gửi JWT đến API Gateway.
  * API Gateway xác thực JWT.
  * Lambda xử lý nghiệp vụ.
  * Amazon RDS lưu trữ và trả dữ liệu.

* Kiểm thử thành công các public API và protected API cơ bản.

* Phát hiện và xử lý một số vấn đề trong quá trình triển khai, bao gồm:

  * Lỗi kết nối Lambda với Amazon RDS.
  * Lỗi Security Group.
  * Lỗi quyền truy cập AWS Secrets Manager.
  * Lỗi cấu hình biến môi trường.
  * Lỗi CORS.
  * Lỗi cấu hình Cognito JWT Authorizer.

* Hoàn thành phần hạ tầng mạng, cơ sở dữ liệu, xác thực và backend API cơ bản của dự án **PharmaCare AI**.

* Chuẩn bị môi trường để tiếp tục triển khai kho hình ảnh sản phẩm, chatbot AI RAG, frontend production, giám sát, sao lưu và bảo mật trong tuần tiếp theo.