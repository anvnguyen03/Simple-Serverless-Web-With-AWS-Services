---
title : "Create Table DynamoDB"
date :  "2025-01-18" 
weight : 3 
chapter : false
pre : " <b> 3. </b> "
---

#### Create Table DynamoDB
In this step, we will create a **DynamoDB** table to store all the product data for the application. The table will serve as the primary database, enabling CRUD (Create, Read, Update, Delete) operations through the **Lambda Function**. Each product will be stored as an item in the table, with attributes such as ID, name, and price. The table will be configured to support efficient data retrieval and interaction through **API Gateway** and **Lambda**.
___
1. From the AWS Management console, search for **DynamoDB** in the search bar and click on **DynamoDB**.
![DynamoDB Service](/images/3-CreateDynamoDBTable/dynamodb-001.png)

2. In the AWS **DynamoDB console**, click on the **Create table** button.
![DynamoDB Service](/images/3-CreateDynamoDBTable/dynamodb-002.png)

3. In the **Create table** tab. Provide the following details:
- **Table name**: Table name: Enter a name for your table (e.g. ProductsTable)
- **Partition Key**: Enter the key named id.
- **Key type**: Select **String** for Partition key.
- Scroll down and click **Create table** button to proceed.
![DynamoDB Service](/images/3-CreateDynamoDBTable/dynamodb-003.png)
![DynamoDB Service](/images/3-CreateDynamoDBTable/dynamodb-004.png)

4. After creating the table, a confirmation message will appear at the top of the screen: the table was successfully created.
![DynamoDB Service](/images/3-CreateDynamoDBTable/dynamodb-005.png)

5. We just have completed creating table for **DynamoDB**!.