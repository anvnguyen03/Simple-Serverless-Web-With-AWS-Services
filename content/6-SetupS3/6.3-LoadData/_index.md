---
title : "Load Data"
date :  "2025-01-18" 
weight : 6
chapter : false
pre : " <b> 6.3. </b> "
---

#### Load Data
In this step, we will upload the static website files (HTML, CSS, JavaScript) into the S3 bucket created in the previous step. This will enable the S3 bucket to serve as a static website hosting platform for the application.
___
1. Ensure you have the following files ready:
- **index.html**: The main file of your website.

- **app.js**: Contains the JavaScript code to interact with the API Gateway.

2. In the **my-product-app** section, navigate to the **Objects** section, then click the **Upload** button.
![S3](/images/6-s3/s3-007.png)

3. In the **Upload** section:
- Click **Add files** button and select your static files (e.g., `index.html`, `app.js`, etc.).

- If you have multiple files organized in folders, click **Add folder**.

- Select the **index.js** file and the **app.js** file from your computer saved. 
  
- Scroll down and click **Upload** to start the process.

4. After uploading the 2 files, a confirmation message will appear at the top of the screen: upload succeeded.
![S3](/images/6-s3/s3-008.png)
   
5. In the **my-product-app** section, navigate to the **Properties** section.
6. Scroll down to the ***Static website hosting*** section. Note: the **Bucket website endpoint** URL to use to check the results on the website (e.g., `http://my-website-static-bucket.s3-website-us-east-1.amazonaws.com`).
![S3](/images/6-s3/s3-009.png)

7. We have completed the **data loading**.