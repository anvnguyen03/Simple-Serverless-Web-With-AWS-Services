---
title : "Giới thiệu"
date :  "2025-01-18" 
weight : 1 
chapter : false
pre : " <b> 1. </b> "
---
**Serverless**
is a cloud computing model where AWS manages the infrastructure, allowing developers to concentrate on writing code and building applications efficiently. It simplifies development by removing the need for server setup and maintenance.

Features of the Serverless model:

- No Server Management: AWS handles infrastructure, so developers can focus solely on application logic.
- Pay-as-You-Go: Costs are based only on usage, including Lambda executions, S3 storage, API Gateway requests, and DynamoDB operations.
- Automatic Scaling: Services scale up or down automatically to match demand, ensuring cost efficiency and consistent performance.
- Fast Deployment: Pre-configured AWS services speed up the development process.
- Ideal Use Cases: Web and mobile applications, lightweight APIs, real-time or batch processing, MVPs, and cost-sensitive projects.

Main components of the application:

- **AWS DynamoDB**: A fully managed NoSQL database for storing and retrieving product data with high performance and scalability.
- **IAM Role for Lambda and DynamoDB**: Manages access permissions for AWS resources to ensure secure interactions between Lambda and DynamoDB.
- **AWS Lambda**: Serves as the backend to handle CRUD operations. Written in Python, these functions interact with DynamoDB to manage product data efficiently.
- **AWS API Gateway**: Acts as a bridge between the frontend and backend by creating RESTful APIs. Offers secure and manageable endpoints for frontend interactions.
- **AWS S3**: Stores static assets for the user interface, such as HTML, CSS, and JavaScript. Simple, cost-effective, and highly reliable storage for hosting the front-end.