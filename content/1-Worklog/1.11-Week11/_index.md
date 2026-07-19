---
title: "Week 11 Worklog"
date: 2026-06-29
weight: 11
chapter: false
pre: " <b> 1.11. </b> "
---


### Week 11 Objectives:

* Review the technical requirements and architecture of the **PharmaCare AI** project.
* Evaluate the Amazon EC2 deployment approach and compare it with a serverless architecture using AWS Lambda.
* Migrate the backend design from a traditional server-based model to a serverless architecture.
* Build the network infrastructure and database environment for the system.
* Develop the backend API and user authentication mechanism.
* Test connectivity between the frontend and AWS services.

### Tasks to be carried out this week:
| Day | Task                                                                                                                                                                                                   | Start Date | Completion Date | Reference Material                        |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ---------- | --------------- | ----------------------------------------- |
| 2   | - Reviewed the requirements and architecture of the **PharmaCare AI** project.<br>- Analyzed the Amazon EC2 deployment approach.<br>- Identified the networking, security, and operational requirements of the system. | 29/06/2026 | 29/06/2026 |
| 3   |- Compared Amazon EC2 with AWS Lambda.<br>- Migrated the backend design to a serverless architecture.<br>- Created a VPC, public subnets, private application subnets, private database subnets, route tables, and security groups. | 30/06/2026 | 30/06/2026 |
| 4   | - Deployed Amazon RDS for PostgreSQL in private database subnets.<br>- Stored database credentials in AWS Secrets Manager.<br>- Created the `pharmacare-db-migration` Lambda function to initialize the database schema. | 01/07/2026 | 01/07/2026 |
| 5   | - Created an Amazon Cognito user pool, an app client, and the Admin and Customer groups.<br>- Developed the `pharmacare-backend-api` Lambda function to handle products, user profiles, shopping carts, and orders. | 02/07/2026 | 02/07/2026 |
| 6   | - Created an Amazon API Gateway HTTP API.<br>- Configured CORS and an Amazon Cognito JWT authorizer.<br>- Created a React frontend using Vite to test authentication, public APIs, and protected APIs.<br>- Compiled the results of the week. | 03/07/2026 | 03/07/2026 |


### Week 11 Achievements:

* Reviewed and adjusted the overall architecture of the **PharmaCare AI** project.

* Analyzed the Amazon EC2 deployment approach and evaluated the operational requirements of a server-based model, including:

  * Operating system configuration.
  * Runtime environment installation.
  * Patch and dependency management.
  * Server status monitoring.
  * Continuous resource maintenance.

* Compared Amazon EC2 with AWS Lambda based on the following criteria:

  * Scalability.
  * Infrastructure administration requirements.
  * Operating costs.
  * Deployment time.
  * Suitability for the project scope.

* Selected a serverless architecture for the backend to reduce server administration tasks and support automatic scaling based on request volume.

* Built the network infrastructure for PharmaCare AI, including:

  * Amazon VPC.
  * Public subnets.
  * Private application subnets.
  * Private database subnets.
  * Route tables.
  * Internet gateway.
  * Security groups.

* Separated the application and database tiers into private subnets to limit direct access from the Internet.

* Successfully deployed Amazon RDS for PostgreSQL in private database subnets.

* Configured a security group to allow only authorized backend resources to connect to Amazon RDS through PostgreSQL port `5432`.

* Used AWS Secrets Manager to encrypt and store database credentials, preventing usernames and passwords from being written directly in the source code.

* Created and configured the `pharmacare-db-migration` Lambda function to:

  * Retrieve database connection information from AWS Secrets Manager.
  * Connect to Amazon RDS for PostgreSQL.
  * Execute database migration statements.
  * Initialize the system’s database tables.

* Created an Amazon Cognito user pool and app client to manage user registration, authentication, and sign-in.

* Created two user groups:

  * Admin.
  * Customer.

* Developed the `pharmacare-backend-api` Lambda function using Node.js to handle the following functional areas:

  * Products.
  * Categories.
  * Stores.
  * User profiles.
  * Shopping carts.
  * Orders.

* Created an Amazon API Gateway HTTP API and integrated it with the backend Lambda function.

* Defined public APIs that can be accessed without authentication, including:

  * Checking backend health.
  * Viewing the product list.
  * Viewing product details.
  * Viewing categories.
  * Viewing the store list.

* Defined protected APIs that require user authentication, including:

  * Viewing a user profile.
  * Managing a shopping cart.
  * Creating orders.
  * Viewing order history.

* Configured an Amazon Cognito JWT authorizer to allow API Gateway to validate tokens before forwarding requests to AWS Lambda.

* Configured CORS to allow the React frontend to send requests to Amazon API Gateway.

* Created a ReactJS application using Vite to test the following workflow:

  * The user signs in through Amazon Cognito.
  * Amazon Cognito issues a JWT to the frontend.
  * The frontend sends the JWT to Amazon API Gateway.
  * API Gateway validates the JWT.
  * AWS Lambda processes the business logic.
  * Amazon RDS stores and returns the required data.

* Successfully tested the basic public and protected APIs.

* Identified and resolved several issues during the deployment process, including:

  * Connectivity errors between AWS Lambda and Amazon RDS.
  * Security group configuration errors.
  * AWS Secrets Manager permission errors.
  * Environment variable configuration errors.
  * CORS errors.
  * Amazon Cognito JWT authorizer configuration errors.

* Completed the core network infrastructure, database, authentication mechanism, and backend API for the **PharmaCare AI** project.

* Prepared the environment for implementing the product image repository, RAG chatbot, production frontend, monitoring, backup, and security components in the following week.