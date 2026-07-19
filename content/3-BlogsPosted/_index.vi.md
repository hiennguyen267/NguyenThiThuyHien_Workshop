---
title: "Các bài blogs đã đăng"
date: 2024-01-01
weight: 3
chapter: false
pre: " <b> 3. </b> "
---


###  [Blog 1 - Tối ưu hóa bảo mật Kubernetes với cơ chế Session Policies trong Amazon EKS Pod Identity](3.1-Blog1/)
Bài viết giới thiệu Amazon EKS Pod Identity kết hợp Session Policies, một cơ chế giúp đơn giản hóa việc quản lý quyền truy cập AWS IAM cho các ứng dụng Kubernetes trên Amazon EKS. Thông qua việc áp dụng Session Policies, quyền truy cập của từng pod có thể được giới hạn linh hoạt mà không cần tạo quá nhiều IAM Role, góp phần giảm độ phức tạp trong quản trị và tăng cường nguyên tắc phân quyền tối thiểu (Least Privilege). Đồng thời, bài viết cũng trình bày kiến trúc hoạt động, các lợi ích nổi bật và một ví dụ ứng dụng trong hệ thống quản lý nhà thuốc triển khai trên Amazon EKS.

###  [Blog 2 - Data Masking trong Amazon RDS for Oracle](3.2-Blog2/)
Bài viết tóm tắt những kiến thức mình tìm hiểu về Data Masking trong Amazon RDS for Oracle dựa trên một bài viết từ AWS Database Blog. Nội dung giải thích lý do cần bảo vệ dữ liệu nhạy cảm trước khi sử dụng trong môi trường phát triển hoặc kiểm thử, giới thiệu khái niệm Data Masking và mô tả quy trình tự động hóa với các dịch vụ AWS như Amazon RDS, EventBridge Scheduler và AWS Secrets Manager. Đồng thời, bài viết nhấn mạnh vai trò của Data Masking trong việc bảo vệ thông tin nhạy cảm nhưng vẫn đảm bảo dữ liệu có thể sử dụng hiệu quả cho phát triển và kiểm thử ứng dụng.

###  [Blog 3 - Tìm hiểu các cập nhật trong hướng dẫn AWS Well-Architected Framework](3.3-Blog3/)
Bài viết tóm tắt những kiến thức mình học được từ bài “Announcing updates to the AWS Well-Architected Framework guidance” trên AWS Architecture Blog. Nội dung giới thiệu mục tiêu của AWS Well-Architected Framework, giải thích sáu trụ cột trong thiết kế kiến trúc Cloud và nhấn mạnh tầm quan trọng của việc đánh giá, cải tiến kiến trúc một cách liên tục thay vì chỉ thực hiện ở giai đoạn triển khai ban đầu. Đồng thời, bài viết cũng chia sẻ những bài học rút ra và cách áp dụng Framework vào dự án PharmaCare AI nhằm nâng cao tính bảo mật, độ tin cậy, hiệu năng, tối ưu chi phí và hiệu quả vận hành hệ thống.