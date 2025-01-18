---
title : "Create Lambda Function"
date :  "2025-01-18" 
weight : 4
chapter : false
pre : " <b> 4.2. </b> "
---

#### Create Lambda Function
In this step, we will create a Lambda Function that handles all the CRUD (Create, Read, Update, Delete) operations for the application. The Lambda Function will serve as the backend, processing requests received from the API Gateway and interacting with S3 to manage product data.
___

1. Search for **Lambda** in the search bar and click on **Lambda**.

2. In the AWS **Lambda console**, click on the **Create a function** button.

3. In the **Create a function**. Provide the following details:
- Choose **“Author from scratch”**.

- **Function name**: Enter a name for your function (e.g. `ProductCRUDFunction`)

- **Runtime**: Select **Python 3.12**

- **Architecture**: Select **x86_64**.

- **Permissions**: Under **Execution role** section, select **Use an existing role**, the system will display the **Existing Role** section, select the IAM Role name that you created earlier in
  [section 4.1.Create IAM Role for Lambda and DynamoDB](4.1-CreateIAMRole) Create IAM Role for Lambda and DynamoDB

- Click **Create function** button to proceed.
![Lambda Fuction](/images/4-lambda/lambda-010.png)
![Lambda Fuction](/images/4-lambda/lambda-011.png)

4. After creating the function, a confirmation message will appear at the top of the screen: the function was successfully created.
5. In the **ProductCRUDFunction** section created, scroll down to the **Code source** section.

- In the source code box:

  + Click to edit the code inline.

  + Replace the default **lambda_function.py** content with the following code:
  
```python
import json
import boto3
from decimal import Decimal

dynamodb = boto3.resource('dynamodb')
table = dynamodb.Table('ProductsTable')

class DecimalEncoder(json.JSONEncoder):
    def default(self, obj):
        if isinstance(obj, Decimal):
            return float(obj)
        return super(DecimalEncoder, self).default(obj)

def lambda_handler(event, context):
    path = event.get("path")
    http_method = event.get("httpMethod")
    body = json.loads(event["body"]) if event.get("body") else None
    query_params = event.get("queryStringParameters")

    if path == "/products" and http_method == "GET":
        return get_all_products()
    elif path == "/products" and http_method == "POST":
        return add_product(body)
    elif path == "/product" and http_method == "GET":
        return get_product(query_params.get("id") if query_params else None)
    elif path == "/product" and http_method == "PUT":
        return update_product(body)
    elif path == "/product" and http_method == "DELETE":
        return delete_product(query_params.get("id") if query_params else None)
    else:
        return build_response(404, {"message": "Endpoint not found"})

def get_all_products():
    try:
        response = table.scan()
        products = response.get("Items", [])
        for product in products:
            product["price"] = float(product["price"])
        return build_response(200, {"products": products})
    except Exception as e:
        return build_response(500, {"message": str(e)})

def add_product(product):
    required_fields = {"id", "name", "price"}
    if not product or not required_fields.issubset(product):
        return build_response(400, {"message": "Missing required fields"})
    try:
        product["price"] = Decimal(str(product["price"]))
        table.put_item(Item=product)
        return build_response(201, {"message": "Product added successfully !", "product": product})
    except Exception as e:
        return build_response(500, {"message": str(e)})

def get_product(product_id):
    if not product_id:
        return build_response(400, {"message": "Product ID is required"})
    try:
        response = table.get_item(Key={"id": product_id})
        if "Item" in response:
            product = response["Item"]
            product["price"] = float(product["price"])
            return build_response(200, {"product": product})
        else:
            return build_response(404, {"message": "Product not found"})
    except Exception as e:
        return build_response(500, {"message": str(e)})

def update_product(updated_product):
    if not updated_product or "id" not in updated_product:
        return build_response(400, {"message": "Product ID is required"})
    try:
        table.update_item(
            Key={"id": updated_product["id"]},
            UpdateExpression="SET #n = :name, price = :price",
            ExpressionAttributeNames={"#n": "name"},
            ExpressionAttributeValues={
                ":name": updated_product["name"],
                ":price": Decimal(str(updated_product["price"])),
            }
        )
        return build_response(200, {"message": "Product updated successfully !"})
    except Exception as e:
        return build_response(500, {"message": str(e)})

def delete_product(product_id):
    if not product_id:
        return build_response(400, {"message": "Product ID is required"})
    try:
        table.delete_item(Key={"id": product_id})
        return build_response(200, {"message": "Product deleted successfully !"})
    except Exception as e:
        return build_response(500, {"message": str(e)})

def build_response(status_code, body):
    return {
        "statusCode": status_code,
        "headers": {
            "Content-Type": "application/json",
            "Access-Control-Allow-Origin": "*",
            "Access-Control-Allow-Methods": "GET, POST, PUT, DELETE, OPTIONS",
        },
        "body": json.dumps(body, cls=DecimalEncoder),
    }

```

  + Click **Deploy (Ctrl+Shift+U)** to save the function. 

6. After saving, the system will display the message: Successfully updated the function **ProductCRUDFunction.**
![Lambda Fuction](/images/4-lambda/lambda-012.png)

7. We have completed creating **Lambda Function**.