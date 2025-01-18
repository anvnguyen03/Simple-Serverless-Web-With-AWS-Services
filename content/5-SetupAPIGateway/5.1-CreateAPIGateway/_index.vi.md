---
title : "Create API Gateway"
date :  "2025-01-18" 
weight : 5
chapter : false
pre : " <b> 5.1. </b> "
---

#### Create API Gateway
In this step of creating an API Gateway, we will create a REST API to act as an interface between the application and the Lambda Function. The API Gateway will define structured endpoints (e.g. /products, /product) to handle HTTP requests like GET, POST, PUT, and DELETE.
___

1. Search for **API Gateway** in the search bar and click on **API Gateway**.

2. In the **Create API**, scroll down **REST API** section, click **Build** button.
![API Gateway](/images/5-apigateway/apigateway-001.png)

3. In the **Create REST API**, provide the following details:
- **API Name:** Enter a name for your API (e.g. `ProductAPI`)

- **Description**: Add an optional description.

- **API Endpoint Type**: Select **Regional**.

- Click **Create API** button to proceed.
![API Gateway](/images/5-apigateway/apigateway-002.png)

4. After creating the REST API, a confirmation message will appear at the top of the screen: Successfully created REST API.
   
5. In the **ProductAPI** section created, navigate to the **Resources** section, click **Create Resource** button.
![API Gateway](/images/5-apigateway/apigateway-003.png)

6. In the **Create resource**, add the following resources:
- **Resource Name**: Enter a name for the resource: `products`

- Click enable **CORS (Cross Origin Resource Sharing)**.

- Click **Create resource** button.
  
{{% notice info %}}
Enable CORS to allow the S3-hosted interface to send requests to API Gateway, since the interface and API Gateway may be on different domains or origins. If CORS is not enabled, the browser will block requests from the S3-hosted interface to the API Gateway due to a violation of the browser’s default security policy, known as the Same-Origin Policy.
{{% /notice %}}
![API Gateway](/images/5-apigateway/apigateway-004.png)

7. After creating the resource, a confirmation message will appear at the top of the screen: Successfully created resource.
![API Gateway](/images/5-apigateway/apigateway-005.png)

8. Similarly, create another resource: `product` like step 6.

9. In the **Resources**, choose `/products` resource and click **Create method** button:
![API Gateway](/images/5-apigateway/apigateway-006.png)

10. In the **Create method, Method details** section provide the following details:
- **GET**:

    + **Method Type**: select **GET**.

    + **Integration Type**: select **Lambda Function**.

    + Click enable **Lambda proxy integration**.

    + Select your current region (e.g. `us-east-1`). Select the Lambda Function name that you created earlier in section 4.2. Create Lambda Function (e.g. `ProductCRUDFunction`)

    + Scroll down and click **Create method** button.

{{% notice info %}}
Enable **Lambda proxy integration**: API Gateway passes all HTTP requests (headers, queries, body, methods) directly to Lambda. Lambda handles all logic and responses. Without enabling **Lambda proxy integration**: API Gateway only sends pre-configured data (Mapping Templates) to Lambda. Parameters and responses must be manually configured in API Gateway.
{{% /notice %}}

![API Gateway](/images/5-apigateway/apigateway-007.png)
![API Gateway](/images/5-apigateway/apigateway-008.png)
![API Gateway](/images/5-apigateway/apigateway-009.png)
___
- After creating the method, a confirmation message will appear at the top of the screen: the method was successfully created.
![API Gateway](/images/5-apigateway/apigateway-010.png)
- Similarly, create a **POST** method for `/products` resource.

11. Similarly, for the `/product` resource, add the following methods:
- **GET**: To fetch a product by ID.

- **PUT**: To update a product.

- **DELETE**: To delete a product.

- Configure **each method** similarly by integrating it with the appropriate **Lambda Functio**n like step: 9, 10.
![API Gateway](/images/5-apigateway/apigateway-011.png)

12. Next we will **Deploy API**.
