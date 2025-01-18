---
title : "Clean Up Resources"
date :  "2025-01-18" 
weight : 8
chapter : false
pre : " <b> 8. </b> "
---
We will take the following steps to delete the resources we created in this guide.

#### Delete DynamoDB
- In the **AWS DynamoDB** console, navigate to the **Tables**.

- Select the table to delete, then click **Delete** button.

- In the **Delete table**, enter in the box: **confirm** and click **Delete** button.

- After deleting the table, a confirmation message will appear at the top of the screen: the table was deleted successfully.
![Clean up](/images/8-cleanup/cleanup-001.png)

#### Delete S3
**Delete Object**

- In the AWS **S3** console, access **my-product-app** section.

- **Select** 2 files: **index.html** and **app.js**, then click **Delete** button.

- In the **Delete Objects**, enter in the box: **permanently delete** and click **Delete objects** button.

- After deleting the object, a confirmation message will appear at the top of the screen: the object was deleted successfully.

**Delete Bucket**

- In the AWS **S3** console, select **my-product-app** section and click **Delete** button.

- In the **Delete bucket**, enter in the bucket name box: **my-product-app** and click **Delete Bucket** button.

- After deleting the bucket, a confirmation message will appear at the top of the screen: the bucket was deleted successfully.

#### Delete Lambda
- In the AWS **Lambda** console, navigate to the **Functions**.

- **Select** the **function** to delete, then click **Actions** button and click **Delete** button.

- In the **Delete 1 functions**, enter in the box: **delete** and click **Delete** button.

#### Delete API Gateway
- In the AWS **API Gateway** console, navigate to the **APIs**.

- **Select** the **API to delete**, then click **Delete** button.

- In the **Delete API**, enter in the box: **confirm** and click **Delete** button.

- After deleting the API, a confirmation message will appear at the top of the screen: the API was deleted successfully.