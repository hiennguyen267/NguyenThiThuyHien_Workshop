---
title: "Blog 1"
date: 2026-07-06
weight: 1
chapter: false
pre: " <b> 3.1. </b> "
---

# Optimizing Kubernetes Security with Session Policies in Amazon EKS Pod Identity

In large-scale Kubernetes environments, managing AWS permissions for every workload is always a critical security challenge. Each application may require different access permissions to AWS services such as Amazon S3, Amazon DynamoDB, Amazon SQS, or other managed services. If permissions are not designed carefully, the system may either become difficult to operate or expose serious security risks due to over-permissioning.

Amazon EKS Pod Identity provides a simpler way for Kubernetes applications running on Amazon EKS to obtain AWS IAM credentials. With the additional support of **Session Policies**, this mechanism becomes more flexible because permissions can be dynamically narrowed for each pod without creating too many independent IAM roles.

### Challenges of the Traditional IRSA Approach

Before EKS Pod Identity, a common approach was to use **IAM Roles for Service Accounts (IRSA)**. IRSA helps Kubernetes workloads access AWS services by associating a Kubernetes ServiceAccount with an IAM Role. Although this approach is useful, it can become complex in large systems.

The first challenge is the rapid growth of IAM Roles. To follow the principle of least privilege, engineers may need to create a separate IAM Role for each microservice or workload. In a large Kubernetes cluster, this can lead to hundreds of IAM Roles, making permission management and security auditing difficult.

The second challenge is operational complexity. Each Kubernetes ServiceAccount must be manually mapped to an IAM Role, often through annotations and configuration files. This increases CI/CD complexity and may introduce human errors during deployment.

The third challenge is over-permissioning. In practice, development teams may reuse a few broad IAM Roles to avoid creating too many separate roles. However, this increases the blast radius because a pod may receive permissions that it does not actually need.

### Amazon EKS Pod Identity with Session Policies

Session Policies in Amazon EKS Pod Identity help solve this problem by allowing administrators to define an inline IAM policy when creating or updating a Pod Identity association. This policy does not grant new permissions. Instead, it narrows down the permissions already granted by the IAM Role.

In other words, the final effective permission is calculated as the intersection between:

* The permissions allowed by the IAM Role.
* The permissions allowed by the Session Policy.

This means that a Session Policy can only reduce permissions, not expand them. As a result, the system can reuse a shared IAM Role while still applying different permission boundaries to different pods.

### Architecture Overview

The following diagram illustrates the authentication and authorization flow of Amazon EKS Pod Identity.

{{< figure src="/NguyenThiThuyHien_Workshop/images/blog/blog1.jpg" title="Amazon EKS Pod Identity Architecture" width="650px" >}}

The architecture can be divided into three main layers.

### 1. Identity Layer

The Identity Layer includes the Amazon EKS cluster, Kubernetes pods, Kubernetes ServiceAccounts, and the EKS Pod Identity Agent running on worker nodes.

In this layer, each pod does not need to directly store AWS credentials or hardcode an IAM Role ARN. Instead, the pod is associated with a Kubernetes ServiceAccount. The EKS Pod Identity Agent is responsible for helping pods retrieve temporary AWS credentials securely.

This approach improves credential isolation and reduces the risk of exposing long-term credentials inside application containers.

### 2. Policy and Control Layer

The Policy and Control Layer is responsible for mapping Kubernetes identities to AWS IAM permissions.

A Pod Identity Association connects a Kubernetes ServiceAccount with an IAM Role. When a pod needs to access AWS resources, the EKS Pod Identity workflow uses AWS Security Token Service to obtain temporary credentials. At this point, a Session Policy can be applied to narrow the permissions for that specific pod or workload.

For example, two pods may use the same IAM Role, but each pod can receive a different Session Policy:

* Pod A can only read objects from a specific Amazon S3 bucket.
* Pod B can only send messages to a specific Amazon SQS queue.
* Pod C can only access selected DynamoDB table actions.

This design reduces the number of IAM Roles that must be created while still maintaining least-privilege access.

### 3. Target Resource Layer

The Target Resource Layer includes AWS services that the pod needs to access, such as:

* Amazon S3
* Amazon DynamoDB
* Amazon SQS
* Other AWS services

These services receive requests signed with temporary AWS credentials. Because the credentials are already scoped down by the Session Policy, the target resources do not need to understand the internal Kubernetes architecture. They only need to evaluate the final IAM permissions attached to the request.

### Benefits of Using Session Policies

The first benefit is simplified IAM management. Instead of creating many IAM Roles for small permission differences, teams can reuse a smaller number of roles and apply Session Policies to restrict access for each workload.

The second benefit is stronger least-privilege enforcement. Since Session Policies can only narrow permissions, they help prevent pods from receiving excessive access.

The third benefit is reduced operational overhead. Cluster administrators and platform teams can manage permissions more centrally through Pod Identity Associations instead of maintaining large numbers of role-to-service-account mappings.

The fourth benefit is better scalability for large Kubernetes environments. In systems with many namespaces, microservices, and teams, reducing the number of IAM Roles can make auditing, governance, and maintenance easier.

### Example Use Case

Consider a pharmacy management system running on Amazon EKS. Multiple microservices may need to access AWS services:

* The product service reads medicine images from Amazon S3.
* The order service writes order events to Amazon SQS.
* The analytics service reads selected tables from Amazon DynamoDB.

Without Session Policies, each service may require a separate IAM Role to maintain least privilege. With EKS Pod Identity and Session Policies, these services can reuse a broader IAM Role, while each pod receives a different scoped-down policy at runtime.

This makes the architecture cleaner and easier to operate while still preserving strong security boundaries.

### Conclusion

Amazon EKS Pod Identity with Session Policies is an important improvement for Kubernetes workload security on AWS. It helps reduce IAM Role sprawl, simplifies permission management, and enforces least privilege more effectively.

Instead of creating many separate IAM Roles for every microservice, platform teams can use a centralized permission model where the IAM Role provides the base permission and Session Policies dynamically narrow access for each pod. This approach is especially useful for large-scale Kubernetes environments where security, scalability, and operational efficiency are equally important.

### References

* Original article: <https://aws.amazon.com/blogs/containers/session-policies-for-amazon-eks-pod-identity/>
* Related article: <https://aws.amazon.com/blogs/containers/amazon-eks-pod-identity-a-new-way-for-applications-on-eks-to-obtain-iam-credentials/>
* Amazon EKS Pod Identity documentation: <https://docs.aws.amazon.com/eks/latest/userguide/pod-identities.html>