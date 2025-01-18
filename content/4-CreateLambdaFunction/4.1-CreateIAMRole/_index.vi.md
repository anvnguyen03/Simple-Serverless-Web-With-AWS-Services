---
title : "Create IAM Role for Lambda and DynamoDB"
date :  "2025-01-18" 
weight : 4
chapter : false
pre : " <b> 4.1. </b> "
---

#### Create IAM Role for Lambda and DynamoDB
In this case, we will create an IAM Role to allow Lambda Function to perform operations on DynamoDB. This IAM Role will help connect Lambda and DynamoDB securely without storing **Access Key** in the source code.
___

1. Search for **IAM** in the search bar and click on **IAM.**
![Lambda Fuction](/images/4-lambda/lambda-001.png)

2. In the IAM Console, go to the **Roles** section. Click the **Create role** button.
![Lambda Fuction](/images/4-lambda/lambda-002.png)

3. In the **Create role**. Provide the following details:
- In step 1: **Select Trusted Entity**:
  + **Trusted entity** type section: Choose **AWS Service**.
  
  + In the **Use case** section: Select **Lambda** as the use case.
  
  + Click **Next** button to continue.
![Lambda Fuction](/images/4-lambda/lambda-003.png)
![Lambda Fuction](/images/4-lambda/lambda-004.png)

- In step 2: **Add permissions**:

  + In the **Permissions policies** section, use the search bar to type `AWSLambda_FullAccess`. When the results appear, select `AWSLambda_FullAccess` by checking the box next to it. This permission allows Lambda Functions to have full access to the services needed to execute code and manage resources on AWS.

  + Next, use the search bar to type `AmazonDynamoDBFullAccess`. When the results appear, select `AmazonDynamoDBFullAccess` by checking the box next to it. This permission allows the **Lambda Function** to perform full operations (Create, Read, Update, Delete) on **DynamoDB**, ensuring efficient interaction with the data table.

  + After, click **Next** button to continue.
![Lambda Fuction](/images/4-lambda/lambda-005.png)
![Lambda Fuction](/images/4-lambda/lambda-006.png)

- In step 3: **Name, review and create**:

  + **Role details** section: Role name: Enter a name for your role (e.g. `role-lambda-dynamo`). Description: Add an optional description.

  + In the **Permission policy summary** section, review the attached policies to ensure they include **AWSLambda_FullAccess** and **AmazonDynamoDBFullAccess**.

  + After, click **Create role** button to proceed.
![Lambda Fuction](/images/4-lambda/lambda-007.png)
![Lambda Fuction](/images/4-lambda/lambda-008.png)

4. After creating the role, a confirmation message will appear at the top of the screen: The role was successfully created.
![Lambda Fuction](/images/4-lambda/lambda-009.png)
   
5. We have completed creating IAM Roles for **Lambda** and **DynamoDB**. Next we will create **Lambda Function**.