---
title: "Blog 3"
date: 2026-07-07
weight: 3
chapter: false
pre: " <b> 3.3. </b> "
---

# Tìm hiểu các cập nhật trong hướng dẫn AWS Well-Architected Framework

Trong quá trình thực tập và tìm hiểu về kiến trúc hệ thống trên AWS, em đã đọc bài viết **“Announcing updates to the AWS Well-Architected Framework guidance”** trên AWS Architecture Blog. Bài viết này giúp em hiểu rằng việc thiết kế một hệ thống cloud trên AWS không chỉ là lựa chọn từng dịch vụ riêng lẻ, mà còn cần đánh giá toàn bộ kiến trúc dựa trên các best practice đã được kiểm chứng.

Điều em thấy thú vị là AWS không xem Well-Architected Framework như một bộ checklist cố định. Thay vào đó, framework này được cập nhật liên tục dựa trên kinh nghiệm triển khai thực tế của nhiều tổ chức trên thế giới. Mục tiêu của framework là giúp kiến trúc sư và kỹ sư cloud thiết kế hệ thống an toàn, đáng tin cậy, hiệu quả, tối ưu chi phí và bền vững.

### AWS Well-Architected Framework là gì?

AWS Well-Architected Framework là tập hợp các best practice về kiến trúc giúp các nhóm kỹ thuật đánh giá và cải thiện workload trên cloud. Framework này cung cấp một cách tiếp cận có cấu trúc để xem xét hệ thống trên nhiều khía cạnh quan trọng.

Theo cách hiểu của em, framework này giúp trả lời các câu hỏi như:

* Hệ thống có đủ an toàn không?
* Hệ thống có thể phục hồi khi xảy ra lỗi không?
* Hệ thống có dễ vận hành và giám sát không?
* Tài nguyên có được sử dụng hiệu quả không?
* Chi phí đã được tối ưu chưa?
* Kiến trúc có cân nhắc yếu tố bền vững không?

Điều này rất quan trọng vì một hệ thống có thể hoạt động bình thường từ góc nhìn người dùng, nhưng vẫn tồn tại các điểm yếu tiềm ẩn về bảo mật, độ tin cậy, giám sát hoặc quản lý chi phí.

### Góc nhìn kiến trúc

Hình bên dưới thể hiện ý tưởng sử dụng hướng dẫn kiến trúc để đánh giá và cải thiện cloud workload.

{{< figure src="/images/blog/blog3.jpg" title="AWS Well-Architected Framework Guidance" width="650px" >}}

Well-Architected Framework giúp các nhóm cloud review workload định kỳ thay vì chỉ kiểm tra kiến trúc một lần ở giai đoạn ban đầu. Cách tiếp cận này hỗ trợ quá trình cải tiến liên tục trong suốt vòng đời của hệ thống.

### Sáu trụ cột của Well-Architected Framework

AWS Well-Architected Framework được xây dựng dựa trên sáu trụ cột:

* Operational Excellence
* Security
* Reliability
* Performance Efficiency
* Cost Optimization
* Sustainability

Các trụ cột này không nên được xem xét tách biệt. Một kiến trúc tốt cần cân bằng tất cả các trụ cột vì việc tối ưu một khía cạnh có thể ảnh hưởng đến khía cạnh khác.

Ví dụ, giảm chi phí quá mức có thể ảnh hưởng đến độ tin cậy. Tăng hiệu năng mà không kiểm soát chi phí có thể gây lãng phí. Bổ sung quá nhiều kiểm soát bảo mật mà không cân nhắc vận hành có thể làm hệ thống khó quản lý hơn.

### 1. Operational Excellence

Operational Excellence tập trung vào việc vận hành và giám sát hệ thống một cách hiệu quả. Trụ cột này bao gồm khả năng hiểu hành vi hệ thống, phát hiện lỗi, phản hồi sự cố và cải thiện quy trình vận hành theo thời gian.

Từ trụ cột này, em học được rằng deploy hệ thống thành công là chưa đủ. Nhóm kỹ thuật còn cần logs, metrics, alarms, dashboards và quy trình vận hành rõ ràng. Những thành phần này giúp kỹ sư phát hiện vấn đề sớm và xử lý nhanh khi có sự cố.

Ví dụ, trong hệ thống cloud, Amazon CloudWatch có thể được sử dụng để thu thập logs và metrics, tạo alarms và hỗ trợ quá trình troubleshooting.

### 2. Security

Trụ cột Security tập trung vào việc bảo vệ dữ liệu, hệ thống và tài sản. Nội dung bao gồm quản lý định danh và quyền truy cập, bảo vệ dữ liệu, bảo mật hạ tầng, phản hồi sự cố và giám sát bảo mật.

Trụ cột này nhắc em rằng bảo mật cần được thiết kế ngay từ đầu. Không nên chỉ bổ sung bảo mật sau khi hệ thống đã được triển khai.

Trong kiến trúc AWS, bảo mật có thể liên quan đến các dịch vụ như AWS IAM, Amazon Cognito, AWS WAF, AWS Secrets Manager, mã hóa và các công cụ giám sát. Các dịch vụ này giúp bảo vệ cả người dùng và tài nguyên backend.

### 3. Reliability

Trụ cột Reliability tập trung vào việc đảm bảo workload có thể hoạt động đúng và phục hồi khi xảy ra lỗi.

Một hệ thống đáng tin cậy cần có khả năng xử lý các lỗi như sự cố máy chủ, lỗi database, gián đoạn mạng hoặc thay đổi lưu lượng truy cập đột ngột. Trên AWS, độ tin cậy có thể được cải thiện thông qua triển khai Multi-AZ, backup, health check, tự động phục hồi và lập kế hoạch disaster recovery.

Trụ cột này giúp em hiểu rằng lỗi không phải là điều nên bỏ qua. Thay vào đó, kiến trúc cần được thiết kế với các kịch bản lỗi ngay từ đầu.

### 4. Performance Efficiency

Performance Efficiency tập trung vào việc sử dụng tài nguyên cloud hiệu quả để đáp ứng yêu cầu của hệ thống.

Trụ cột này không chỉ nói về việc chọn máy chủ mạnh. Hiệu năng còn liên quan đến việc chọn đúng dịch vụ, sử dụng caching, tối ưu truy cập database, chọn mô hình compute phù hợp và điều chỉnh tài nguyên theo nhu cầu workload.

Ví dụ, Amazon CloudFront có thể cải thiện hiệu năng phân phối frontend, trong khi AWS Lambda có thể cung cấp khả năng xử lý backend có thể mở rộng mà không cần quản lý server.

### 5. Cost Optimization

Cost Optimization tập trung vào việc tránh các chi phí không cần thiết nhưng vẫn đáp ứng yêu cầu kỹ thuật và nghiệp vụ.

Trụ cột này đặc biệt quan trọng khi học AWS bằng credit hoặc ngân sách giới hạn. Tài nguyên cloud có thể phát sinh chi phí nếu không được giám sát hoặc dọn dẹp đúng cách.

Thông qua trụ cột này, em học được rằng kỹ sư nên sử dụng các công cụ như AWS Budgets, Cost Explorer và giám sát tài nguyên để kiểm soát chi phí. Tối ưu chi phí nên được cân nhắc ngay từ giai đoạn thiết kế, không chỉ sau khi chi phí đã tăng cao.

### 6. Sustainability

Sustainability tập trung vào việc giảm tác động môi trường của cloud workload.

Trụ cột này cho thấy kiến trúc cloud cũng cần cân nhắc việc sử dụng tài nguyên có trách nhiệm. Tránh cấp phát thừa tài nguyên, tắt tài nguyên không sử dụng và lựa chọn các dịch vụ hiệu quả có thể hỗ trợ cả sustainability và cost optimization.

Điều này giúp em hiểu rằng kiến trúc hiệu quả không chỉ có lợi cho hiệu năng và chi phí, mà còn có ý nghĩa đối với trách nhiệm môi trường trong dài hạn.

### Điều em thấy ấn tượng

Một điểm em thấy ấn tượng là Well-Architected Framework luôn được cập nhật để phản ánh xu hướng công nghệ mới, cải tiến dịch vụ AWS và kinh nghiệm thực tế từ khách hàng.

Điều này có nghĩa là việc review kiến trúc cloud không nên được xem là nhiệm vụ làm một lần. Khi hệ thống phát triển, yêu cầu thay đổi, lưu lượng tăng và rủi ro mới xuất hiện. Vì vậy, kiến trúc cũng cần được đánh giá và cải thiện liên tục.

Một điểm quan trọng khác là sáu trụ cột cần được xem xét đồng thời. Một hệ thống an toàn nhưng quá tốn kém có thể không thực tế. Một hệ thống chi phí thấp nhưng không đáng tin cậy có thể không đáp ứng nhu cầu nghiệp vụ. Một hệ thống có hiệu năng tốt nhưng khó vận hành có thể tạo ra rủi ro lâu dài.

### Những điều em học được

Sau khi đọc bài viết này, em rút ra một số bài học quan trọng.

Thứ nhất, AWS Well-Architected Framework cung cấp một phương pháp có cấu trúc để đánh giá kiến trúc cloud.

Thứ hai, review kiến trúc nên là một quá trình liên tục trong suốt vòng đời hệ thống, không chỉ là một checklist trước khi triển khai.

Thứ ba, sáu trụ cột cần được xem xét cùng nhau vì các quyết định kiến trúc cloud thường có sự đánh đổi.

Thứ tư, implementation guidance rất quan trọng vì kỹ sư cần các khuyến nghị có thể áp dụng thực tế, không chỉ các nguyên tắc chung.

Cuối cùng, cloud engineer nên thường xuyên review workload và cải thiện kiến trúc dựa trên các best practice đã được cập nhật.

### Liên hệ với dự án PharmaCare AI

Bài viết này có ý nghĩa với dự án **PharmaCare AI** của em vì hệ thống được thiết kế trên AWS và bao gồm nhiều lớp như frontend, authentication, API, database, AI chatbot, monitoring và backup.

Sáu trụ cột có thể được áp dụng vào dự án như sau:

* **Operational Excellence:** sử dụng Amazon CloudWatch logs và alarms để giám sát hành vi hệ thống.
* **Security:** sử dụng Amazon Cognito, AWS IAM, AWS WAF và AWS Secrets Manager để bảo vệ người dùng và tài nguyên backend.
* **Reliability:** sử dụng Amazon RDS Multi-AZ, AWS Backup và các managed services để tăng tính sẵn sàng của hệ thống.
* **Performance Efficiency:** sử dụng Amazon CloudFront, AWS Lambda và Amazon OpenSearch Service để cải thiện thời gian phản hồi.
* **Cost Optimization:** giám sát tài nguyên AWS và dọn dẹp các dịch vụ không sử dụng để tránh chi phí không cần thiết.
* **Sustainability:** tránh cấp phát thừa tài nguyên và ưu tiên sử dụng serverless services khi phù hợp.

Thông qua bài viết này, em hiểu rằng thiết kế PharmaCare AI không chỉ là làm cho website chạy được. Hệ thống còn cần an toàn, đáng tin cậy, dễ quan sát, có kiểm soát chi phí và có khả năng bảo trì lâu dài.

### Kết luận

Bài viết trên AWS Architecture Blog về các cập nhật của AWS Well-Architected Framework guidance giúp em hiểu rõ hơn tư duy thiết kế kiến trúc của AWS.

Một kiến trúc cloud tốt không nên chỉ tập trung vào từng dịch vụ riêng lẻ. Kiến trúc cần được đánh giá trên nhiều khía cạnh, bao gồm vận hành, bảo mật, độ tin cậy, hiệu năng, chi phí và sustainability.

Bài học giá trị nhất đối với em là việc review kiến trúc là một quá trình liên tục. Khi hệ thống phát triển, kiến trúc cũng cần được đánh giá và cải thiện thường xuyên. Đây là tư duy quan trọng để xây dựng các hệ thống cloud thực tế ổn định, an toàn, hiệu quả và sẵn sàng cho vận hành lâu dài.

### Tài liệu tham khảo

* AWS Architecture Blog: <https://aws.amazon.com/blogs/architecture/announcing-updates-to-the-aws-well-architected-framework-guidance/>
* AWS Well-Architected Framework: <https://aws.amazon.com/architecture/well-architected/>
* AWS Well-Architected Tool: <https://aws.amazon.com/well-architected-tool/>