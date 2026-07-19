---
title: "Blog 2"
date: 2026-07-07
weight: 2
chapter: false
pre: " <b> 3.2. </b> "
---

# Data Masking in Amazon RDS for Oracle

During my internship and learning process about AWS Database services, I read an interesting article about **Data Masking in Amazon RDS for Oracle**. This was a new topic for me, so I wanted to summarize and share what I learned from it.

Previously, I thought that when a Development or UAT environment was needed, the team could simply restore a backup or snapshot from the Production database. However, after reading this article, I realized that this approach can expose a large amount of sensitive customer data if there is no proper protection mechanism.

Sensitive data may include:

* Full name
* Email address
* Phone number
* Home address
* Other personally identifiable information

If this data is moved directly to Development or Testing environments without protection, it can create serious security and compliance risks.

### What is Data Masking?

Based on my understanding, **Data Masking** is the process of replacing real sensitive data with fictitious data while keeping the same format and structure. This allows the system to continue working normally for development or testing purposes, but developers and testers cannot see the real customer information.

For example:

| Original Data | After Masking |
| --- | --- |
| Nguyen Van A | Customer001 |
| loc@gmail.com | user001@example.com |
| 0909123456 | 0909XXXXXX |

With this approach, development and testing teams can still use realistic data for application testing, but sensitive customer information is protected.

### Workflow Overview

The following diagram illustrates the high-level workflow of data masking for Amazon RDS for Oracle.

{{< figure src="/NguyenThiThuyHien_Workshop/images/blog/blog2.jpg" title="Data Masking Workflow in Amazon RDS for Oracle" width="650px" >}}

When reviewing this workflow, I understood the process as follows.

### 1. EventBridge Scheduler

Amazon EventBridge Scheduler can be used to trigger the workflow automatically based on a defined schedule. This helps reduce manual operations whenever the team needs to refresh data for a lower environment such as Development or UAT.

### 2. Restore Snapshot

The system restores a snapshot from the Production database into a temporary Amazon RDS for Oracle instance. This temporary database is used as the target environment for the masking process.

This step is important because data masking should not be performed directly on the Production database. Instead, the masking process should be executed on a cloned or restored database instance.

### 3. AWS Secrets Manager

Instead of storing usernames and passwords directly in scripts, database credentials can be retrieved securely from **AWS Secrets Manager**. This is a safer approach because sensitive information is not hardcoded in source code or automation scripts.

Using Secrets Manager also supports better credential management and reduces the risk of accidental exposure.

### 4. Perform Data Masking

After the database is restored, the masking process is executed on the cloned Amazon RDS for Oracle instance. The masking script replaces sensitive information with fictitious values while preserving the structure and usability of the data.

For Oracle workloads, data masking can be performed using Oracle Data Masking and Subsetting Pack through Oracle Enterprise Manager. The goal is to produce realistic but non-sensitive data for non-production use.

### 5. Create a New Snapshot

After the data masking process is completed, the system creates a new snapshot from the masked RDS instance. This snapshot contains protected data and can be used safely for non-production environments.

### 6. Restore for Development or UAT

Finally, the masked snapshot is restored as a database instance for Development, Testing, or UAT environments. Developers and testers can use this database for application work without directly accessing real customer information.

### AWS Services Involved

What I found interesting is that the solution does not only focus on masking data. It also combines multiple AWS services to automate and secure the overall workflow.

Some services that can be involved include:

* Amazon RDS for Oracle
* Amazon EventBridge Scheduler
* AWS Step Functions
* AWS Systems Manager
* AWS Secrets Manager
* Amazon EC2 for Oracle Enterprise Manager deployment
* Amazon S3 or snapshot storage depending on the implementation approach

Each service has a specific responsibility. Together, they help automate the workflow, reduce manual tasks, and improve operational consistency.

### What I Learned

After studying this topic, I learned several important lessons.

First, Production data should not be used directly in Development or Testing environments without protection. Even if the environment is internal, sensitive information can still be exposed.

Second, Data Masking is an effective method to protect sensitive data while still keeping the data useful for testing and development.

Third, AWS Secrets Manager helps manage credentials more securely than storing usernames and passwords in scripts or source code.

Fourth, automation with AWS services can save time, reduce manual mistakes, and make the data refresh process more repeatable.

Finally, data protection is not only about access control and encryption. It is also about how data is handled when it is copied, restored, or shared across different environments.

### Conclusion

Data Masking in Amazon RDS for Oracle is a practical topic that helped me understand more about data security in real cloud systems. It shows that protecting data is not limited to Production environments only. Development, Testing, and UAT environments also need proper security controls.

Through this article, I realized that when building systems on AWS, teams must carefully consider how sensitive data is processed outside Production. Data Masking is one useful approach that helps balance security and usability.

This topic gave me a better understanding of how AWS and Oracle database tools can work together to support secure database operations in real-world enterprise systems.

### References

* AWS Database Blog: <https://aws.amazon.com/blogs/database/data-masking-in-amazon-rds-for-oracle/>
* Amazon RDS for Oracle documentation: <https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/CHAP_Oracle.html>
* AWS Secrets Manager documentation: <https://docs.aws.amazon.com/secretsmanager/latest/userguide/intro.html>