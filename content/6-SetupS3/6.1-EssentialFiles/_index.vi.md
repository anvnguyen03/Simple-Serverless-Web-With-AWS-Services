---
title : "Essential Project Files"
date :  "2025-01-18" 
weight : 6
chapter : false
pre : " <b> 6.1. </b> "
---

In this step, we will create the key files needed for the frontend of our application. These include:

- **index.html**: This file sets up the structure and design of the user interface. It includes a form for adding or updating products, a list to display them, and buttons for editing or deleting products. Simple CSS is used to make the page look clean and modern.

- **app.js**: This file contains the JavaScript code to handle product actions like adding, updating, fetching, and deleting through the API Gateway. It also updates the user interface based on user actions.

These files are important for building the frontend and making the application functional for managing products.
___
1. In the **index.html** file, paste the following code:
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Product Manager</title>
    <style>
        body {
            font-family: 'Roboto', Arial, sans-serif;
            background-color: #f8f9fa;
            margin: 0;
            padding: 0;
        }
        .container {
            max-width: 800px;
            margin: 40px auto;
            background: #ffffff;
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0px 4px 6px rgba(0, 0, 0, 0.1);
        }
        h1 {
            text-align: center;
            color: #333333;
            text-transform: uppercase;
        }
        .product-form {
            background: #f4f4f4;
            padding: 20px;
            border-radius: 8px;
            margin-bottom: 20px;
        }
        .product-form h3 {
            margin-bottom: 15px;
            color: #555555;
        }
        .product-form input {
            width: calc(100% - 22px);
            padding: 10px;
            margin-bottom: 10px;
            border: 1px solid #cccccc;
            border-radius: 5px;
            font-size: 14px;
        }
        .product-form button {
            width: 100%;
            padding: 10px;
            background: #28a745;
            color: #ffffff;
            border: none;
            margin: 15px 0;
            border-radius: 5px;
            font-size: 16px;
            cursor: pointer;
            transition: background-color 0.3s ease;
        }
        .product-form button:hover {
            background: #218838;
        }
        .product-list {
            margin-top: 20px;
        }
        .product-list h3 {
            font-size: 25px;
            color: #555555;
            margin: 35px 0 20px 0;
            text-align: center;
            text-transform: uppercase;
        }
        .product-list table {
            width: 100%;
            border-collapse: collapse;
            margin-top: 10px;
            background: #ffffff;
            overflow: hidden;
            border-radius: 8px;
            box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
        }
        .product-list th {
            background: #545454;
            color: #ffffff;
            padding: 12px;
            text-align: center;
            font-size: 14px;
            border: 1px solid #fff;
        }
        .product-list td {
            border: 1px solid #c9c9c9;
            padding: 10px;
            font-size: 14px;
            color: #333333;
            text-align: center;
        }
        .product-list tr:nth-child(odd) {
            background-color: #f8f9fa;
        }
        .product-list tr:nth-child(even) {
            background-color: #ffffff;
        }
        .product-list td:last-child {
            text-align: center;
        }
        .product-list button {
            padding: 5px 10px;
            color: #ffffff;
            border: none;
            border-radius: 3px;
            font-size: 12px;
            cursor: pointer;
            transition: background-color 0.3s ease;
        }
        .product-list .delete-button {
            background: #dc3545;
            padding: 10px;
            color: #ffffff;
            border: none;
            margin: 15px 0;
            border-radius: 5px;
            font-size: 16px;
            cursor: pointer;
            transition: background-color 0.3s ease;
        }
        .product-list .delete-button:hover {
            background: #c82333;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>Product Manager</h1>
        <div class="product-form">
            <h3>Add or Update Product</h3>
            <input type="text" id="productId" placeholder="Product ID">
            <input type="text" id="productName" placeholder="Product Name">
            <input type="number" id="productPrice" placeholder="Product Price">
            <button onclick="addOrUpdateProduct()">Add or Update Product</button>
        </div>
        <div class="product-list">
            <h3>Product List</h3>
            <table>
                <thead>
                    <tr>
                        <th>ID</th>
                        <th>Name</th>
                        <th>Price</th>
                        <th>Actions</th>
                    </tr>
                </thead>
                <tbody id="productTableBody">
                </tbody>
            </table>
        </div>
    </div>
    
    <script src="app.js"></script>
</body>
</html>
```
___
2. In the **app.js** file, paste the following code:
```javascript
const apiUrl = "https://m6leha6hvk.execute-api.us-east-1.amazonaws.com/prod";

async function getAllProducts() {
    try {
        const response = await fetch(`${apiUrl}/products`);
        const data = await response.json();
        renderProducts(data.products || []);
    } catch (error) {
        console.error("Error fetching products:", error);
    }
}

async function addOrUpdateProduct() {
    const id = document.getElementById("productId").value;
    const name = document.getElementById("productName").value;
    const price = document.getElementById("productPrice").value;

    if (!id || !name || !price) {
        alert("Please fill all fields");
        return;
    }

    const product = { id, name, price: Number(price) };
    const existingProduct = await fetch(`${apiUrl}/product?id=${id}`).then(res => res.ok ? res.json() : null);

    try {
        if (existingProduct && existingProduct.product) {
            const response = await fetch(`${apiUrl}/product`, {
                method: "PUT",
                headers: { "Content-Type": "application/json" },
                body: JSON.stringify(product),
            });
            const result = await response.json();
            alert(result.message || "Product updated successfully !");
        } else {
            const response = await fetch(`${apiUrl}/products`, {
                method: "POST",
                headers: { "Content-Type": "application/json" },
                body: JSON.stringify(product),
            });
            const result = await response.json();
            alert(result.message || "Product added successfully !");
        }
        getAllProducts();
    } catch (error) {
        console.error("Error saving product:", error);
    }
}

async function deleteProduct(productId) {
    if (!confirm("Are you sure you want to delete this product?")) return;

    try {
        const response = await fetch(`${apiUrl}/product?id=${productId}`, {
            method: "DELETE",
        });
        const result = await response.json();
        if (response.ok) {
            alert(result.message || "Product deleted successfully !");
            getAllProducts();
        } else {
            alert(result.message || "Failed to delete product");
        }
    } catch (error) {
        console.error("Error deleting product:", error);
    }
}

function renderProducts(products) {
    const tableBody = document.getElementById("productTableBody");
    tableBody.innerHTML = "";

    products.forEach((product) => {
        const row = document.createElement("tr");

        row.innerHTML = `
            <td>${product.id}</td>
            <td>${product.name}</td>
            <td>${product.price}</td>
            <td>
                <button class="delete-button" onclick="deleteProduct('${product.id}')">Delete</button>
            </td>
        `;

        tableBody.appendChild(row);
    });
}

window.onload = () => {
    getAllProducts();
};
```

3. We have completed uploading the **essential project files**. Next we will create **S3**.
{{% notice info %}}
In the line var apiUrl = “https://m6leha6hvk.execute-api.us-east-1.amazonaws.com/prod"; replace https://m6leha6hvk.execute-api.us-east-1.amazonaws.com/prod with the **Invoke URL** from your **API Gateway deployed** in [section 5.2. DeployAPI](a). This URL connects your UI to the server, allowing your application to perform actions such as adding, updating, retrieving, and deleting data efficiently.
{{% /notice %}}