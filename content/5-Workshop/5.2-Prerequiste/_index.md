---
title : "Prepare backend code"
date : 2026-07-01 
weight : 2 
chapter : false
pre : " <b> 5.2. </b> "
---

#### Purpose

In this step, you package the backend source code and upload it to Amazon S3. CloudFormation will later use this uploaded package to create Lambda functions automatically.

#### 1. Build backend code locally

1. Open Terminal or Command Prompt.
2. Move to the backend folder:

```bash
cd "C:\Users\Sieu chu nhiem\Desktop\aws-serverless-event-portal\backend"
```

3. Install dependencies:

```bash
npm install
```

4. Build TypeScript source code into JavaScript:

```bash
npm run build
```

5. After the build completes, the backend folder will contain a `dist` folder.
6. Copy `package.json` and `node_modules` into the `dist` folder.
7. Compress all files inside `dist` into a Lambda deployment package named `backend-code.zip`.

#### 2. Create an S3 bucket for backend package

Open the Amazon S3 console and create a bucket in the **Asia Pacific (Singapore) ap-southeast-1** Region. In this workshop, the backend package was uploaded to a temporary package bucket named `eventapp-backend-package-ap-southeast-1`.

#### 3. Upload backend package

Open the bucket, choose **Upload**, select the `backend-code.zip` package, and upload it to S3.

#### 4. Copy the S3 URI

After the upload succeeds, open the uploaded object and copy the **S3 URI**. This value will be used in `template.yaml` for the Lambda `CodeUri` values.

Example S3 URI:

```text
s3://eventapp-backend-package-ap-southeast-1/backend-code.zip
```

After this step, keep the backend package S3 URI carefully and continue to the CloudFormation deployment step.
