---
title : "Preparation"
date :  "2025-01-18" 
weight : 2 
chapter : false
pre : " <b> 2. </b> "
---
#### AWS Account
{{% notice info %}}
You will need an AWS account to do this lab. If you don’t have one, please sign up for an AWS account.
{{% /notice %}}
To learn how to create an AWS account, you can refer to:
- [Creating your first AWS account](https://000001.awsstudygroup.com/)

#### Basic files
- File index.html: User interface.
- File app.js: Send request to API Gateway.

#### Necessary tools
**Source code editor**:
- Visual Studio Code – A free, powerful, and extensible source code editor, ideal for serverless application development. Use it to build the user interface in index.html and handle API requests in app.js to communicate with API Gateway.
- Install Visual Studio Code from [Visual Studio Code official website.](https://code.visualstudio.com/)

**API Testing Tools**:
- Postman – A user-friendly tool for testing API Gateway by sending requests and validating responses from the serverless application.
- Install Postman from [Postman official website.](https://www.postman.com/)

#### Activate services:
- **AWS DynamoDB**: Provide a fast and scalable NoSQL database for managing and storing application data.
- **IAM Role for Lambda and DynamoDB**: IAM Role to allow Lambda Function to perform operations on DynamoDB.
- **AWS Lambda**: Execute backend code to handle application logic and interact with the database.
- **Amazon API Gateway**: Manage RESTful API endpoints to connect the frontend with backend services.
- **AWS S3**: Store and serve static content such as HTML, CSS, and JavaScript for the application interface.