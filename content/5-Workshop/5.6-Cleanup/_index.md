---
title : "Clean up resources"
date : 2024-01-01
weight : 6
chapter : false
pre : " <b> 5.6. </b> "
---

Congratulations on completing this workshop. After testing the Event Portal deployment, the final step is to clean up the AWS resources that were created during the lab. This helps avoid unnecessary costs from temporary S3 buckets, CloudFormation resources, and networking components.

#### 1. Delete CloudFormation stack

1. Open AWS CloudFormation.
2. Select the stack `EventApp-Backend-System`.
3. Choose **Delete stack**.
4. Confirm the deletion and wait until the stack is removed.

CloudFormation will delete the backend resources it created, such as Lambda functions, API Gateway, DynamoDB tables, Cognito resources, IAM roles, and related configuration.

![Confirm CloudFormation stack deletion](/images/5-Workshop/event-portal/12-delete-backend-stack-confirm.png)

#### 2. Empty and delete S3 buckets

1. Open Amazon S3.
2. Select the frontend bucket from CloudFormation Outputs.
3. Empty the bucket before deleting it.
4. Delete the bucket after it becomes empty.

If a CloudFormation template bucket or temporary backend package bucket was created during the workshop, empty it first before deleting the bucket.

![Empty temporary S3 bucket](/images/5-Workshop/event-portal/09-empty-template-bucket-confirm.png)

After the objects are removed, check that the empty operation succeeds.

![Temporary S3 bucket emptied successfully](/images/5-Workshop/event-portal/10-empty-template-bucket-success.png)

Then delete the bucket and verify that only the required buckets remain.

![Temporary S3 bucket deleted](/images/5-Workshop/event-portal/11-template-bucket-deleted.png)

#### 3. Delete backend package bucket

If you created a separate S3 bucket to store the backend package, delete the uploaded backend package first, then delete the bucket.

Example backend package bucket:

```text
buketbackend
```

#### 4. Delete networking resources if created

If the workshop created extra networking resources such as a NAT Gateway, remove them after the application is no longer needed. This is important because NAT Gateway can continue generating charges while it remains active.

![Delete NAT Gateway](/images/5-Workshop/event-portal/13-delete-nat-gateway.png)

#### 5. Remove local build artifacts

You can also remove temporary local build artifacts if they are no longer needed:

- Backend `dist` package
- `backend-code.zip` or `backend.rar`
- Frontend `dist` folder

After cleanup, the workshop resources are removed and the AWS account will no longer be charged for the deployed project.
