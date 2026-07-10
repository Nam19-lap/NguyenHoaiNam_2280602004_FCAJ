---
title : "Update template.yaml"
date : 2026-07-01
weight : 1
chapter : false
pre : " <b> 5.3.1. </b> "
---

#### Purpose

CloudFormation needs to know where the Lambda deployment package is stored. Because the backend package was uploaded to S3, update the `CodeUri` values in `template.yaml` before creating the stack.

#### Steps

1. Open `template.yaml` in the backend folder using VS Code or another editor.
2. Use `Ctrl + F` to search for:

```yaml
CodeUri: dist/
```

3. Replace each `dist/` value with the S3 URI copied from the backend package.

Example:

```yaml
CodeUri: s3://eventapp-backend-package-ap-southeast-1/backend-code.zip
```

4. Save the file.

#### Notes

- The template contains multiple Lambda functions, so update every `CodeUri` occurrence.
- The S3 URI must point to the backend `.zip` package uploaded to S3.
- Keep the file saved locally because it will be uploaded to CloudFormation in the next step.
