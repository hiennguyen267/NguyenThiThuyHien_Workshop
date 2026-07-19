---
title: "Blog 3"
date: 2026-07-07
weight: 3
chapter: false
pre: " <b> 3.3. </b> "
---

# Understanding Updates to the AWS Well-Architected Framework Guidance

During my internship and learning process about AWS architecture, I read an article on the AWS Architecture Blog titled **“Announcing updates to the AWS Well-Architected Framework guidance.”** This article helped me understand that designing a cloud system on AWS is not only about selecting individual services, but also about evaluating the entire architecture based on proven best practices.

What I found interesting is that AWS does not treat the Well-Architected Framework as a fixed checklist. Instead, the framework is continuously updated based on real-world implementation experience from many organizations around the world. Its purpose is to help architects and cloud engineers design systems that are secure, reliable, efficient, cost-optimized, and sustainable.

### What is the AWS Well-Architected Framework?

The AWS Well-Architected Framework is a set of architectural best practices that helps teams review and improve cloud workloads. It provides a structured way to evaluate whether a system is designed properly across different important areas.

In my understanding, the framework helps answer questions such as:

* Is the system secure enough?
* Can the system recover from failures?
* Is the system easy to operate and monitor?
* Are resources being used efficiently?
* Is the cost optimized?
* Does the architecture consider sustainability?

This is important because a system may work correctly from the user’s perspective, but still have hidden weaknesses in security, reliability, monitoring, or cost management.

### Architecture Perspective

The following image represents the idea of using architectural guidance to review and improve cloud workloads.

{{< figure src="/NguyenThiThuyHien_Workshop/images/blog/blog3.jpg" title="AWS Well-Architected Framework Guidance" width="650px" >}}

The Well-Architected Framework helps cloud teams review workloads regularly instead of only checking the architecture once at the beginning. This approach supports continuous improvement throughout the system lifecycle.

### The Six Pillars of the Well-Architected Framework

The AWS Well-Architected Framework is built around six pillars:

* Operational Excellence
* Security
* Reliability
* Performance Efficiency
* Cost Optimization
* Sustainability

These pillars should not be considered separately. A good architecture needs to balance all of them because improving one area may affect another.

For example, reducing cost too aggressively may reduce reliability. Improving performance without cost control may increase unnecessary spending. Adding many security controls without considering operations may make the system harder to manage.

### 1. Operational Excellence

Operational Excellence focuses on running and monitoring systems effectively. It includes the ability to understand system behavior, detect issues, respond to incidents, and improve operations over time.

From this pillar, I learned that deploying a system successfully is not enough. The team also needs logs, metrics, alarms, dashboards, and clear operational procedures. These elements help engineers detect problems early and respond quickly when incidents occur.

For example, in a cloud system, Amazon CloudWatch can be used to collect logs and metrics, create alarms, and support troubleshooting activities.

### 2. Security

The Security pillar focuses on protecting data, systems, and assets. It includes identity and access management, data protection, infrastructure protection, incident response, and security monitoring.

This pillar reminded me that security should be designed from the beginning. It should not be added only after the system has already been deployed.

In AWS architecture, security can involve services such as AWS IAM, Amazon Cognito, AWS WAF, AWS Secrets Manager, encryption, and monitoring tools. These services help protect both users and backend resources.

### 3. Reliability

The Reliability pillar focuses on ensuring that a workload can perform correctly and recover from failures.

A reliable system should be able to handle failures such as server issues, database problems, network interruptions, or unexpected traffic changes. In AWS, reliability can be improved through Multi-AZ deployment, backups, health checks, automated recovery, and disaster recovery planning.

This pillar helped me understand that failure is not something to ignore. Instead, architecture should be designed with failure scenarios in mind.

### 4. Performance Efficiency

Performance Efficiency focuses on using cloud resources efficiently to meet system requirements.

This pillar is not only about choosing powerful servers. It is also about selecting the right services, using caching, optimizing database access, choosing appropriate compute models, and adjusting resources based on workload demand.

For example, Amazon CloudFront can improve frontend delivery performance, while AWS Lambda can provide scalable backend processing without managing servers.

### 5. Cost Optimization

Cost Optimization focuses on avoiding unnecessary costs while still meeting technical and business requirements.

This pillar is especially important when learning AWS with credits or limited budgets. Cloud resources can generate cost if they are not monitored or cleaned up properly.

Through this pillar, I learned that engineers should use tools such as AWS Budgets, Cost Explorer, and resource monitoring to control spending. Cost optimization should be considered during the design stage, not only after the bill becomes high.

### 6. Sustainability

Sustainability focuses on reducing the environmental impact of cloud workloads.

This pillar shows that cloud architecture should also consider responsible resource usage. Avoiding over-provisioning, shutting down unused resources, and choosing efficient services can support both sustainability and cost optimization.

This helped me understand that efficient architecture is not only beneficial for performance and cost, but also for long-term environmental responsibility.

### What I Found Interesting

One point that impressed me is that the Well-Architected Framework is continuously updated to reflect new technology trends, AWS service improvements, and real-world customer experience.

This means cloud architecture review should not be treated as a one-time task. As a system grows, requirements change, traffic increases, and risks evolve. Therefore, the architecture should also be reviewed and improved continuously.

Another important point is that the six pillars should be considered together. A system that is secure but too expensive may not be practical. A system that is low-cost but unreliable may not meet business needs. A system that performs well but is difficult to operate may become risky in the long term.

### What I Learned

After reading the article, I learned several important lessons.

First, the AWS Well-Architected Framework provides a structured method for evaluating cloud architecture.

Second, architecture review should be a continuous process throughout the system lifecycle, not only a checklist before deployment.

Third, the six pillars need to be considered together because cloud architecture decisions often involve trade-offs.

Fourth, implementation guidance is important because engineers need practical recommendations, not only general principles.

Finally, cloud engineers should regularly review workloads and improve architecture based on updated best practices.

### Relation to My PharmaCare AI Project

This article is useful for my **PharmaCare AI** project because the system is designed on AWS and includes multiple layers such as frontend, authentication, API, database, AI chatbot, monitoring, and backup.

The six pillars can be applied to the project as follows:

* **Operational Excellence:** use Amazon CloudWatch logs and alarms to monitor system behavior.
* **Security:** use Amazon Cognito, AWS IAM, AWS WAF, and AWS Secrets Manager to protect users and backend resources.
* **Reliability:** use Amazon RDS Multi-AZ, AWS Backup, and managed services to improve system availability.
* **Performance Efficiency:** use Amazon CloudFront, AWS Lambda, and Amazon OpenSearch Service to improve response time.
* **Cost Optimization:** monitor AWS resources and clean up unused services to avoid unnecessary cost.
* **Sustainability:** avoid over-provisioning and use serverless services where suitable.

Through this article, I understood that designing PharmaCare AI is not only about making the website work. The system also needs to be secure, reliable, observable, cost-aware, and maintainable.

### Conclusion

The AWS Architecture Blog article about updates to the AWS Well-Architected Framework guidance helped me better understand the architectural mindset of AWS.

A good cloud architecture should not only focus on individual services. It should be reviewed across multiple dimensions, including operations, security, reliability, performance, cost, and sustainability.

The most valuable lesson for me is that architecture review is a continuous process. As a system grows, its architecture must also be reviewed and improved regularly. This mindset is important for building real-world cloud systems that are stable, secure, efficient, and ready for long-term operation.

### References

* AWS Architecture Blog: <https://aws.amazon.com/blogs/architecture/announcing-updates-to-the-aws-well-architected-framework-guidance/>
* AWS Well-Architected Framework: <https://aws.amazon.com/architecture/well-architected/>
* AWS Well-Architected Tool: <https://aws.amazon.com/well-architected-tool/>