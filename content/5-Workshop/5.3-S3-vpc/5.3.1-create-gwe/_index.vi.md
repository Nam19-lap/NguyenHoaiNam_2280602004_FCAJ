---
title : "Cập nhật template.yaml"
date : 2026-07-01
weight : 1
chapter : false
pre : " <b> 5.3.1. </b> "
---

#### Mục đích

CloudFormation cần biết Lambda deployment package đang nằm ở đâu. Vì backend package đã được upload lên S3, ta cần cập nhật các giá trị `CodeUri` trong `template.yaml` trước khi tạo stack.

#### Các bước thực hiện

1. Mở file `template.yaml` trong thư mục backend bằng VS Code hoặc trình soạn thảo khác.
2. Nhấn `Ctrl + F` và tìm:

```yaml
CodeUri: dist/
```

3. Thay từng giá trị `dist/` bằng S3 URI của backend package đã copy từ S3.

Ví dụ:

```yaml
CodeUri: s3://eventapp-backend-package-ap-southeast-1/backend-code.zip
```

4. Lưu file lại.

#### Lưu ý

- Template có nhiều Lambda functions, vì vậy cần cập nhật tất cả các dòng `CodeUri`.
- S3 URI phải trỏ đúng đến backend package dạng `.zip` đã upload lên S3.
- Sau khi chỉnh sửa, giữ file này để upload lên CloudFormation ở bước tiếp theo.
