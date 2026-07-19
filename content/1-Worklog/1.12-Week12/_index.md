---
title: "Week 12 Worklog"
date: 2026-07-06
weight: 12
chapter: false
pre: " <b> 1.12. </b> "
---



### Week 12 Objectives:

* Complete the remaining features of the **PharmaCare AI** project.
* Develop a pharmaceutical information chatbot using the Retrieval-Augmented Generation (RAG) approach.
* Integrate the chatbot into the React frontend.
* Deploy the frontend using Amazon S3 and Amazon CloudFront.
* Implement basic monitoring, alerting, backup, and security mechanisms.
* Test the main functional flows and connectivity between system components.
* Compile supporting screenshots and complete the internship documentation.

### Tasks to be carried out this week:
| Day | Task                                                                                                                                                                                                   | Start Date | Completion Date | Reference Material                        |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ---------- | --------------- | ----------------------------------------- |
| 2   | - Created a private S3 bucket for storing product images.<br>- Uploaded images to the `products/` prefix, created a CloudFront distribution, and updated the image URLs in Amazon RDS using a Lambda migration function. | 06/07/2026 | 06/07/2026 |
| 3   | - Created an S3 bucket for storing the chatbot knowledge base.<br>- Organized documents into FAQ, product information, health articles, medical guides, and medication safety categories.<br>- Configured Amazon Bedrock, Amazon OpenSearch Serverless, IAM roles, and VPC endpoints. | 07/07/2026 | 07/07/2026 |
| 4   | - Developed the `pharmacare-rag-indexing` Lambda function.<br>- Read documents from Amazon S3, split the content into chunks, generated embeddings using Cohere Embed Multilingual, and stored the vectors in Amazon OpenSearch Serverless. | 08/07/2026 | 08/07/2026 |
| 5   | - Developed the `pharmacare-rag-chatbot` Lambda function.<br>- Generated a vector embedding for each user question, retrieved the three most relevant content chunks, and returned the results with references.<br>- Integrated the chatbot into the React frontend. | 09/07/2026 | 09/07/2026 |
| 6   | - Built the React frontend and deployed it using Amazon S3 and Amazon CloudFront.<br>- Configured Amazon Cognito callback URLs, CloudWatch Logs, CloudWatch alarms, an SNS topic, AWS Backup, and AWS WAF.<br>- Tested the system and compiled supporting screenshots. | 10/07/2026 | 10/07/2026 |


### Week 12 Achievements:

* Completed the storage of product images in Amazon S3.

* Kept the S3 bucket private and distributed the product images through Amazon CloudFront.

* Updated the CloudFront image URLs in the product records stored in Amazon RDS by using a Lambda migration function.

* Created a chatbot knowledge base in Amazon S3 and organized the documents into the following categories:

  * Frequently asked questions.
  * Product information.
  * Health articles.
  * Usage instructions.
  * Pharmaceutical safety information.

* Configured **Cohere Embed Multilingual** on Amazon Bedrock to generate vector embeddings for Vietnamese documents and user questions.

* Created an Amazon OpenSearch Serverless vector search collection to store and query vector data.

* Configured Amazon OpenSearch Serverless to operate within a private network through a VPC endpoint.

* Created a dedicated IAM role for the RAG Lambda functions and granted the required permissions to:

  * Read documents from Amazon S3.
  * Invoke embedding models on Amazon Bedrock.
  * Write and query data in Amazon OpenSearch Serverless.
  * Write execution logs to Amazon CloudWatch Logs.

* Developed the `pharmacare-rag-indexing` Lambda function to perform the following process:

  * Read documents from Amazon S3.
  * Normalize the document content.
  * Split the documents into chunks.
  * Generate vector embeddings.
  * Store vectors, content, and metadata in Amazon OpenSearch Serverless.

* Tested the Lambda indexing function and achieved the following results:

  * Successfully processed 250 documents.
  * Generated 1,186 chunks.
  * Successfully stored the data in the Amazon OpenSearch Serverless vector store.

* Developed the `pharmacare-rag-chatbot` Lambda function to:

  * Receive questions from users.
  * Validate input data.
  * Generate vector embeddings for user questions.
  * Retrieve the three most relevant document chunks.
  * Return results with references to the source documents.

* Configured the chatbot to operate primarily in RAG-only mode with `ENABLE_LLM=false` during testing to reduce token usage and costs.

* Prepared the option to use Amazon Nova Micro by setting `ENABLE_LLM=true` when natural-language answer generation is required.

* Integrated the chatbot interface into the React frontend and verified that users could submit questions, receive results, and view source references.

* Built the React frontend using Vite and generated the production deployment files in the `dist` directory.

* Uploaded the frontend files to a private S3 bucket and distributed the website through Amazon CloudFront over HTTPS.

* Configured CloudFront custom error responses for HTTP status codes `403` and `404` to support React Router.

* Updated the callback and sign-out URLs in Amazon Cognito to support authentication on the deployed frontend.

* Configured Amazon CloudWatch Logs for the following Lambda functions:

  * `pharmacare-backend-api`.
  * `pharmacare-db-migration`.
  * `pharmacare-rag-indexing`.
  * `pharmacare-rag-chatbot`.

* Created CloudWatch alarms to monitor:

  * Amazon RDS CPU utilization.
  * API 5xx errors.
  * Backend Lambda execution errors.
  * Chatbot Lambda execution errors.

* Created the `pharmacare-alert-topic` Amazon SNS topic for sending notifications to the administrator.

* Created an AWS Backup plan for Amazon RDS with a daily backup schedule.

* Enabled AWS WAF Core Protections for CloudFront to help detect and mitigate abnormal web requests.

* Reviewed the IAM roles and IAM policies used by the backend and AI Lambda functions according to the **principle of least privilege**.

* Tested the main functional flows of the system, including:

  * User registration and authentication through Amazon Cognito.
  * Accessing public APIs.
  * Accessing protected APIs using JWTs.
  * Viewing product lists and product details.
  * Managing user profiles.
  * Managing shopping carts.
  * Creating and viewing orders.
  * Displaying product images through Amazon CloudFront.
  * Asking questions and receiving results from the RAG chatbot.

* Verified connectivity between the main system components:

  * React frontend → Amazon Cognito.
  * React frontend → Amazon API Gateway.
  * Amazon API Gateway → AWS Lambda.
  * AWS Lambda → AWS Secrets Manager.
  * AWS Lambda → Amazon RDS.
  * AWS Lambda → Amazon Bedrock.
  * AWS Lambda → Amazon OpenSearch Serverless.
  * Amazon CloudFront → Amazon S3.

* Compiled supporting screenshots and completed the workshop documentation for deploying the **PharmaCare AI** project.

* Completed a working demonstration of the main PharmaCare AI features on AWS.

### Incomplete Tasks and Future Development

* The registration and integration of a custom domain using Amazon Route 53 have not yet been completed.

* A Continuous Integration/Continuous Deployment (CI/CD) pipeline has not yet been implemented.

* Terraform or AWS CloudFormation has not yet been used to manage the infrastructure as code.

* Load testing with a large number of concurrent users has not yet been performed.

* A complete Amazon RDS recovery test from a recovery point has not yet been conducted.

* The Amazon SNS email subscription must be confirmed before alert notifications can be received.

* The AWS WAF rules require further monitoring in Count or Monitor mode before they are changed to Block mode.

* The chatbot was tested primarily in RAG-only mode. The use of Amazon Nova Micro requires further evaluation regarding answer quality, quotas, and operating costs.

### Week 12 Self-Assessment

* Completed the primary objectives established for the week.

* Applied practical knowledge of Amazon S3, Amazon CloudFront, AWS Lambda, Amazon Bedrock, Amazon OpenSearch Serverless, Amazon CloudWatch, Amazon SNS, AWS Backup, and AWS WAF.

* Improved the ability to integrate multiple AWS services into a unified system.

* Improved troubleshooting skills related to IAM policies, data access policies, VPC endpoints, security groups, and private network connectivity.

* Improved skills in system testing, compiling supporting evidence, and writing technical documentation.

* Recognized the need to continue developing knowledge of Infrastructure as Code, CI/CD, performance testing, cost optimization, and production system operations.

* Completed the 12-week internship program and established a foundation for pursuing career paths such as:

  * Cloud Engineer.
  * DevOps Engineer.