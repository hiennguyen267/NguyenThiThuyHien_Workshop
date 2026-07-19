---
title: "Blog 2"
date: 2026-07-07
weight: 2
chapter: false
pre: " <b> 3.2. </b> "
---

# Data Masking trong Amazon RDS for Oracle

Trong quá trình thực tập và tìm hiểu về các dịch vụ AWS Database, em có đọc được một bài viết khá hay về **Data Masking trong Amazon RDS for Oracle**. Đây là một chủ đề khá mới đối với em, nên em muốn tóm tắt và chia sẻ lại những gì mình học được từ bài viết này.

Trước đây, em nghĩ rằng khi cần tạo môi trường Development hoặc UAT thì chỉ cần restore một bản backup hoặc snapshot từ database Production là đủ. Tuy nhiên, sau khi tìm hiểu bài viết này, em nhận ra rằng cách làm đó có thể làm lộ rất nhiều dữ liệu nhạy cảm của khách hàng nếu không có cơ chế bảo vệ phù hợp.

Các dữ liệu nhạy cảm có thể bao gồm:

* Họ và tên
* Email
* Số điện thoại
* Địa chỉ
* Các thông tin cá nhân khác

Nếu những dữ liệu này được đưa trực tiếp sang môi trường Development hoặc Testing mà không được bảo vệ, hệ thống có thể phát sinh nhiều rủi ro về bảo mật và tuân thủ.

### Data Masking là gì?

Theo em hiểu, **Data Masking** là quá trình thay thế dữ liệu nhạy cảm thật bằng dữ liệu giả nhưng vẫn giữ nguyên định dạng và cấu trúc dữ liệu. Nhờ vậy, hệ thống vẫn có thể hoạt động bình thường cho mục đích phát triển hoặc kiểm thử, nhưng lập trình viên và tester sẽ không nhìn thấy thông tin thật của khách hàng.

Ví dụ:

| Dữ liệu gốc | Sau khi Mask |
| --- | --- |
| Nguyễn Văn A | Customer001 |
| loc@gmail.com | user001@example.com |
| 0909123456 | 0909XXXXXX |

Với cách làm này, đội ngũ phát triển và kiểm thử vẫn có dữ liệu gần giống thực tế để sử dụng, nhưng thông tin nhạy cảm của khách hàng được bảo vệ tốt hơn.

### Tổng quan quy trình hoạt động

Sơ đồ bên dưới minh họa quy trình tổng quan của Data Masking cho Amazon RDS for Oracle.

{{< figure src="/NguyenThiThuyHien_Workshop/images/blog/blog2.jpg" title="Data Masking Workflow in Amazon RDS for Oracle" width="650px" >}}

Khi xem quy trình này, em hiểu các bước hoạt động chính như sau.

### 1. EventBridge Scheduler

Amazon EventBridge Scheduler có thể được sử dụng để tự động kích hoạt workflow theo lịch đã cấu hình. Điều này giúp giảm thao tác thủ công mỗi khi cần làm mới dữ liệu cho các môi trường thấp hơn như Development hoặc UAT.

### 2. Restore Snapshot

Hệ thống sẽ restore một snapshot từ database Production thành một Amazon RDS for Oracle instance tạm thời. Database tạm này sẽ được sử dụng làm môi trường đích để thực hiện quá trình masking.

Bước này rất quan trọng vì không nên thực hiện Data Masking trực tiếp trên database Production. Thay vào đó, quá trình masking nên được thực hiện trên một database đã được clone hoặc restore từ snapshot.

### 3. AWS Secrets Manager

Thay vì lưu username và password trực tiếp trong script, thông tin đăng nhập database có thể được lấy an toàn từ **AWS Secrets Manager**. Đây là cách tiếp cận an toàn hơn vì thông tin nhạy cảm không bị hardcode trong source code hoặc script tự động hóa.

Việc sử dụng Secrets Manager cũng giúp quản lý credential tốt hơn và giảm nguy cơ lộ thông tin đăng nhập ngoài ý muốn.

### 4. Thực hiện Data Masking

Sau khi database được restore, quá trình masking sẽ được thực hiện trên Amazon RDS for Oracle instance đã clone. Masking script sẽ thay thế các thông tin nhạy cảm bằng dữ liệu giả nhưng vẫn giữ cấu trúc và khả năng sử dụng của dữ liệu.

Đối với Oracle workload, Data Masking có thể được thực hiện bằng Oracle Data Masking and Subsetting Pack thông qua Oracle Enterprise Manager. Mục tiêu là tạo ra dữ liệu giống thật nhưng không chứa thông tin nhạy cảm để sử dụng cho môi trường non-production.

### 5. Tạo Snapshot mới

Sau khi quá trình Data Masking hoàn tất, hệ thống sẽ tạo một snapshot mới từ RDS instance đã được mask dữ liệu. Snapshot này chứa dữ liệu đã được bảo vệ và có thể được sử dụng an toàn cho các môi trường non-production.

### 6. Restore cho môi trường Development hoặc UAT

Cuối cùng, snapshot đã được mask sẽ được restore thành database instance dành cho môi trường Development, Testing hoặc UAT. Developer và tester có thể sử dụng database này để phát triển và kiểm thử ứng dụng mà không truy cập trực tiếp vào dữ liệu thật của khách hàng.

### Các dịch vụ AWS được sử dụng

Điều em thấy hay là giải pháp này không chỉ tập trung vào việc che giấu dữ liệu mà còn kết hợp nhiều dịch vụ AWS để tự động hóa và bảo mật toàn bộ quy trình.

Một số dịch vụ có thể được sử dụng gồm:

* Amazon RDS for Oracle
* Amazon EventBridge Scheduler
* AWS Step Functions
* AWS Systems Manager
* AWS Secrets Manager
* Amazon EC2 để triển khai Oracle Enterprise Manager
* Amazon S3 hoặc snapshot storage tùy theo cách triển khai

Mỗi dịch vụ đảm nhận một nhiệm vụ riêng. Khi kết hợp lại, chúng giúp tự động hóa quy trình, giảm thao tác thủ công và tăng tính nhất quán trong vận hành.

### Những điều em học được

Sau khi tìm hiểu chủ đề này, em rút ra một số bài học quan trọng.

Thứ nhất, không nên sử dụng trực tiếp dữ liệu Production cho môi trường Development hoặc Testing nếu chưa có biện pháp bảo vệ. Ngay cả khi môi trường đó chỉ dùng nội bộ, dữ liệu nhạy cảm vẫn có thể bị lộ.

Thứ hai, Data Masking là một giải pháp hiệu quả để bảo vệ dữ liệu nhạy cảm nhưng vẫn đảm bảo dữ liệu có thể sử dụng cho kiểm thử và phát triển.

Thứ ba, AWS Secrets Manager giúp quản lý thông tin đăng nhập an toàn hơn so với việc lưu username và password trong script hoặc source code.

Thứ tư, việc tự động hóa bằng các dịch vụ AWS giúp tiết kiệm thời gian, giảm lỗi thủ công và làm cho quy trình làm mới dữ liệu dễ lặp lại hơn.

Cuối cùng, bảo vệ dữ liệu không chỉ dừng lại ở phân quyền và mã hóa. Việc dữ liệu được xử lý như thế nào khi bị sao chép, restore hoặc chia sẻ sang môi trường khác cũng rất quan trọng.

### Kết luận

Data Masking trong Amazon RDS for Oracle là một chủ đề thực tế giúp em hiểu rõ hơn về bảo mật dữ liệu trong các hệ thống cloud. Chủ đề này cho thấy việc bảo vệ dữ liệu không chỉ áp dụng cho môi trường Production, mà còn cần được chú ý trong các môi trường Development, Testing và UAT.

Qua bài viết này, em nhận ra rằng khi xây dựng hệ thống trên AWS, các nhóm phát triển cần cân nhắc kỹ cách xử lý dữ liệu nhạy cảm khi dữ liệu được đưa ra khỏi Production. Data Masking là một phương pháp hữu ích giúp cân bằng giữa yêu cầu bảo mật và nhu cầu sử dụng dữ liệu cho kiểm thử.

Chủ đề này giúp em có thêm góc nhìn về cách AWS và các công cụ Oracle Database có thể phối hợp để hỗ trợ vận hành database an toàn trong các hệ thống doanh nghiệp thực tế.

### Tài liệu tham khảo

* AWS Database Blog: <https://aws.amazon.com/blogs/database/data-masking-in-amazon-rds-for-oracle/>
* Tài liệu Amazon RDS for Oracle: <https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/CHAP_Oracle.html>
* Tài liệu AWS Secrets Manager: <https://docs.aws.amazon.com/secretsmanager/latest/userguide/intro.html>