---
title : "Dọn dẹp tài nguyên"
date : 2026-07-01
weight : 6
chapter : false
pre : " <b> 5.6. </b> "
---

Chúc mừng bạn đã hoàn thành workshop. Sau khi kiểm tra deployment của Event Portal, bước cuối cùng là dọn dẹp các tài nguyên AWS đã tạo trong quá trình thực hành. Việc này giúp tránh phát sinh chi phí không cần thiết từ S3 bucket tạm, CloudFormation resources và các thành phần networking.

#### 1. Xóa CloudFormation stack

1. Mở AWS CloudFormation.
2. Chọn stack `EventApp-Backend-System`.
3. Chọn **Delete stack**.
4. Xác nhận xóa và chờ đến khi stack được remove hoàn toàn.

CloudFormation sẽ xóa các backend resources mà nó đã tạo, ví dụ Lambda functions, API Gateway, DynamoDB tables, Cognito resources, IAM roles và các cấu hình liên quan.

![Xác nhận xóa CloudFormation stack](/images/5-Workshop/event-portal/12-delete-backend-stack-confirm.png)

#### 2. Empty và xóa các S3 bucket

1. Mở Amazon S3.
2. Chọn frontend bucket lấy từ CloudFormation Outputs.
3. Empty bucket trước khi xóa.
4. Xóa bucket sau khi bucket đã trống.

Nếu trong quá trình workshop có tạo CloudFormation template bucket hoặc bucket tạm để chứa backend package, hãy empty bucket trước rồi mới xóa bucket.

![Empty S3 bucket tạm](/images/5-Workshop/event-portal/09-empty-template-bucket-confirm.png)

Sau khi xóa object bên trong bucket, kiểm tra lại trạng thái empty đã thành công.

![Empty S3 bucket thành công](/images/5-Workshop/event-portal/10-empty-template-bucket-success.png)

Tiếp theo, xóa bucket và kiểm tra danh sách bucket còn lại.

![S3 bucket tạm đã được xóa](/images/5-Workshop/event-portal/11-template-bucket-deleted.png)

#### 3. Xóa backend package bucket

Nếu bạn tạo một S3 bucket riêng để chứa backend package, hãy xóa backend package đã upload trước, sau đó xóa bucket.

Ví dụ backend package bucket:

```text
buketbackend
```

#### 4. Xóa networking resources nếu có tạo

Nếu workshop có tạo thêm tài nguyên networking như NAT Gateway, hãy xóa sau khi không còn sử dụng ứng dụng. Đây là bước quan trọng vì NAT Gateway vẫn có thể phát sinh chi phí nếu để hoạt động.

![Xóa NAT Gateway](/images/5-Workshop/event-portal/13-delete-nat-gateway.png)

#### 5. Xóa build artifacts ở local

Có thể xóa thêm các build artifacts ở local nếu không còn cần dùng:

- Backend `dist` package
- `backend-code.zip` hoặc `backend.rar`
- Frontend `dist` folder

Sau khi cleanup, các tài nguyên của workshop đã được xóa và tài khoản AWS sẽ không còn bị tính phí cho project đã triển khai.
