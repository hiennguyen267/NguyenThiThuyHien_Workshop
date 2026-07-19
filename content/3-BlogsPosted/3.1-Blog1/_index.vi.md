---
title: "Blog 1"
date: 2026-07-06
weight: 1
chapter: false
pre: " <b> 3.1. </b> "
---

# Tối ưu hóa bảo mật Kubernetes với cơ chế Session Policies trong Amazon EKS Pod Identity

Trong các môi trường Kubernetes quy mô lớn, việc quản lý quyền truy cập AWS cho từng workload luôn là một thách thức quan trọng về bảo mật. Mỗi ứng dụng có thể cần các quyền khác nhau để truy cập các dịch vụ AWS như Amazon S3, Amazon DynamoDB, Amazon SQS hoặc các dịch vụ được quản lý khác. Nếu thiết kế quyền không cẩn thận, hệ thống có thể trở nên khó vận hành hoặc tạo ra rủi ro bảo mật do cấp quyền quá rộng.

Amazon EKS Pod Identity cung cấp một cơ chế đơn giản hơn để các ứng dụng chạy trên Amazon EKS có thể lấy AWS IAM credentials. Khi kết hợp với **Session Policies**, cơ chế này trở nên linh hoạt hơn vì quyền truy cập có thể được thu hẹp động cho từng Pod mà không cần tạo quá nhiều IAM Role riêng biệt.

### Thách thức của cơ chế IRSA truyền thống

Trước khi có EKS Pod Identity, một cách tiếp cận phổ biến là sử dụng **IAM Roles for Service Accounts (IRSA)**. IRSA giúp workload trong Kubernetes truy cập dịch vụ AWS bằng cách liên kết Kubernetes ServiceAccount với IAM Role. Mặc dù cách tiếp cận này hữu ích, nhưng nó có thể trở nên phức tạp trong các hệ thống lớn.

Thách thức đầu tiên là sự bùng nổ số lượng IAM Role. Để tuân thủ nguyên tắc đặc quyền tối thiểu, kỹ sư có thể phải tạo một IAM Role riêng cho từng microservice hoặc từng workload. Trong một cụm Kubernetes lớn, số lượng IAM Role có thể tăng lên hàng trăm, gây khó khăn cho việc quản lý quyền và audit bảo mật.

Thách thức thứ hai là độ phức tạp trong vận hành. Mỗi Kubernetes ServiceAccount cần được ánh xạ thủ công với một IAM Role, thường thông qua annotation và các file cấu hình. Điều này làm tăng độ phức tạp của CI/CD và dễ phát sinh lỗi trong quá trình triển khai.

Thách thức thứ ba là rủi ro lạm dụng quyền. Trên thực tế, các nhóm phát triển có thể dùng chung một vài IAM Role có quyền rộng để tránh việc phải tạo quá nhiều Role riêng. Tuy nhiên, điều này làm tăng phạm vi ảnh hưởng nếu một Pod bị khai thác, vì Pod có thể nhận nhiều quyền hơn mức thực sự cần thiết.

### Amazon EKS Pod Identity kết hợp Session Policies

Session Policies trong Amazon EKS Pod Identity giúp giải quyết vấn đề này bằng cách cho phép quản trị viên định nghĩa một inline IAM policy khi tạo hoặc cập nhật Pod Identity Association. Chính sách này không cấp thêm quyền mới. Thay vào đó, nó thu hẹp quyền đã được IAM Role cấp sẵn.

Nói cách khác, quyền hiệu lực cuối cùng được tính là phần giao giữa:

* Quyền được IAM Role cho phép.
* Quyền được Session Policy cho phép.

Điều này có nghĩa là Session Policy chỉ có thể giảm quyền, không thể mở rộng quyền. Nhờ đó, hệ thống có thể tái sử dụng một IAM Role dùng chung nhưng vẫn áp dụng các giới hạn quyền khác nhau cho từng Pod.

### Tổng quan kiến trúc

Sơ đồ bên dưới minh họa luồng xác thực và phân quyền của Amazon EKS Pod Identity.

{{< figure src="/images/blog/blog1.jpg" title="Amazon EKS Pod Identity Architecture" width="650px" >}}

Kiến trúc này có thể được chia thành ba lớp chính.

### 1. Identity Layer - Lớp định danh

Identity Layer bao gồm Amazon EKS Cluster, Kubernetes Pod, Kubernetes ServiceAccount và EKS Pod Identity Agent chạy trên worker node.

Trong lớp này, mỗi Pod không cần lưu AWS credentials trực tiếp và cũng không cần hardcode ARN của IAM Role trong container. Thay vào đó, Pod được gắn với một Kubernetes ServiceAccount. EKS Pod Identity Agent sẽ hỗ trợ Pod lấy temporary AWS credentials một cách an toàn.

Cách tiếp cận này giúp cải thiện khả năng cô lập credentials và giảm rủi ro lộ thông tin đăng nhập dài hạn trong container ứng dụng.

### 2. Policy and Control Layer - Lớp chính sách và điều khiển

Policy and Control Layer chịu trách nhiệm ánh xạ định danh Kubernetes sang quyền IAM trên AWS.

Một Pod Identity Association sẽ liên kết Kubernetes ServiceAccount với một IAM Role. Khi Pod cần truy cập tài nguyên AWS, luồng EKS Pod Identity sẽ sử dụng AWS Security Token Service để lấy temporary credentials. Tại thời điểm này, Session Policy có thể được áp dụng để thu hẹp quyền cho Pod hoặc workload cụ thể.

Ví dụ, hai Pod có thể dùng chung một IAM Role nhưng nhận các Session Policy khác nhau:

* Pod A chỉ được đọc dữ liệu từ một Amazon S3 bucket cụ thể.
* Pod B chỉ được gửi message vào một Amazon SQS queue cụ thể.
* Pod C chỉ được thực hiện một số thao tác nhất định trên bảng DynamoDB.

Thiết kế này giúp giảm số lượng IAM Role cần tạo nhưng vẫn duy trì nguyên tắc đặc quyền tối thiểu.

### 3. Target Resource Layer - Lớp tài nguyên đích

Target Resource Layer bao gồm các dịch vụ AWS mà Pod cần truy cập, chẳng hạn như:

* Amazon S3
* Amazon DynamoDB
* Amazon SQS
* Các dịch vụ AWS khác

Các dịch vụ này nhận request được ký bằng temporary AWS credentials. Vì credentials đã được thu hẹp quyền bởi Session Policy, tài nguyên đích không cần hiểu cấu trúc Kubernetes bên trong. Chúng chỉ cần đánh giá quyền IAM cuối cùng được gắn với request.

### Lợi ích khi sử dụng Session Policies

Lợi ích đầu tiên là đơn giản hóa quản lý IAM. Thay vì tạo nhiều IAM Role chỉ để xử lý các khác biệt nhỏ về quyền, nhóm vận hành có thể tái sử dụng số lượng Role ít hơn và dùng Session Policies để giới hạn quyền cho từng workload.

Lợi ích thứ hai là tăng cường thực thi nguyên tắc đặc quyền tối thiểu. Vì Session Policies chỉ có thể thu hẹp quyền, chúng giúp hạn chế việc Pod nhận các quyền dư thừa.

Lợi ích thứ ba là giảm operational overhead. Quản trị viên cụm và platform team có thể quản lý quyền tập trung thông qua Pod Identity Associations thay vì duy trì quá nhiều ánh xạ giữa Role và ServiceAccount.

Lợi ích thứ tư là cải thiện khả năng mở rộng trong môi trường Kubernetes lớn. Với các hệ thống có nhiều namespace, nhiều microservice và nhiều nhóm phát triển, việc giảm số lượng IAM Role giúp quá trình audit, governance và bảo trì dễ dàng hơn.

### Tình huống ứng dụng thực tế

Giả sử một hệ thống quản lý nhà thuốc được triển khai trên Amazon EKS. Nhiều microservice có thể cần truy cập các dịch vụ AWS khác nhau:

* Product service đọc hình ảnh thuốc từ Amazon S3.
* Order service ghi sự kiện đơn hàng vào Amazon SQS.
* Analytics service đọc một số bảng được chọn trong Amazon DynamoDB.

Nếu không dùng Session Policies, mỗi service có thể cần một IAM Role riêng để đảm bảo least privilege. Khi dùng EKS Pod Identity kết hợp Session Policies, các service này có thể tái sử dụng một IAM Role nền tảng, trong khi mỗi Pod nhận một policy thu hẹp quyền khác nhau tại runtime.

Nhờ đó, kiến trúc trở nên gọn hơn, dễ vận hành hơn nhưng vẫn giữ được ranh giới bảo mật chặt chẽ.

### Kết luận

Amazon EKS Pod Identity kết hợp Session Policies là một cải tiến quan trọng cho bảo mật workload Kubernetes trên AWS. Cơ chế này giúp giảm bùng nổ IAM Role, đơn giản hóa quản lý quyền và thực thi nguyên tắc đặc quyền tối thiểu hiệu quả hơn.

Thay vì tạo nhiều IAM Role riêng cho từng microservice, platform team có thể sử dụng một mô hình phân quyền tập trung hơn, trong đó IAM Role cung cấp quyền nền tảng và Session Policies thu hẹp quyền động cho từng Pod. Cách tiếp cận này đặc biệt phù hợp với các môi trường Kubernetes quy mô lớn, nơi bảo mật, khả năng mở rộng và hiệu quả vận hành đều là các yêu cầu quan trọng.

### Tài liệu tham khảo

* Bài viết gốc: <https://aws.amazon.com/blogs/containers/session-policies-for-amazon-eks-pod-identity/>
* Bài viết liên quan: <https://aws.amazon.com/blogs/containers/amazon-eks-pod-identity-a-new-way-for-applications-on-eks-to-obtain-iam-credentials/>
* Tài liệu Amazon EKS Pod Identity: <https://docs.aws.amazon.com/eks/latest/userguide/pod-identities.html>