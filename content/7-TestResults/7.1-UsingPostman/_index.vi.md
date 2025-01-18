---
title : "Using Postman"
date :  "2025-01-18" 
weight : 7
chapter : false
pre : " <b> 7.1. </b> "
---

Postman is a popular tool used to test APIs. Follow the steps below to test your deployed API:

1. **Open Postman**: Make sure you followed [section 2. Preparation Steps]() to download and install Postman. If you have already downloaded and installed it, open it.

2. **Create New Request**: Click **Blank collection**, name your new collection.

3. **Set the URL**: In the URL field, copy the Invoke URL from your deployed API Gateway. For example: `https://<your-api-id>.execute-api.<region>.amazonaws.com/<stage>/<endpoint>`
![Test Results](/images/7-test/test-001.png)

4. Show product list:
- Select the **GET** method.

- Paste the copied URL and add `/products`.

- Click **Send**.

- **Result**: Display product list (currently no products)
![Test Results](/images/7-test/test-002.png)
  
5. Add a new product:
- Select the **POST** method.

- Paste the copied URL and add `/products`.

- Navigate to **Body**, select raw and select **JSON**.

- Fill in product information:
```json
{  
    "id": "101",
    "name": "Laptop Levono",
    "price": "50000",
}
```
- Click **Send**.

- **Result**: Displays a message that the new product was successfully added.
![Test Results](/images/7-test/test-003.png)

6. Test the others API with **POST, PUT, DELETE** method with the same way above