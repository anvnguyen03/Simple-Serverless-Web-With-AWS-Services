---
title : "Deploy API"
date :  "2025-01-18" 
weight : 5
chapter : false
pre : " <b> 5.2. </b> "
---

#### Deploy API
After creating the RESTful API, we will deploy it to make the endpoints publicly accessible. This involves creating a new Stage (e.g., prod), which allows the API Gateway to process requests and route them to the connected Lambda Function. This step ensures the API is ready for use and integration with the application.
___

1. In the **Resources** section, click **Deploy API** button.
![API Gateway](/images/5-apigateway/apigateway-012.png)

2. In the **Deploy API** section, Provide the following details:
- **Stage**: Select **New stage**.

- **Stage Name**: Enter a name for your stage (e.g. `prod`)

- **Description**: Add a deployment description (optional).

- Click **Deploy** button.
![API Gateway](/images/5-apigateway/apigateway-013.png)

3. After creating the stage, a confirmation message will appear at the top of the screen: Successfully created deployment for **ProductAPI**. Note the **Invoke URL** for the deployed API (e.g., `https://{api-id}.execute-api.{region}.amazonaws.com/prod`).
![API Gateway](/images/5-apigateway/apigateway-014.png)

4. We have completed the **API deployment**.