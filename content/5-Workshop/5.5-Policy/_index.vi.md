---
title : "Kiểm tra kết quả triển khai"
date : 2026-07-01
weight : 5
chapter : false
pre : " <b> 5.5. </b> "
---

#### Checklist kiểm tra

Sau khi hoàn tất triển khai, cần kiểm tra hệ thống Event Portal hoạt động đầy đủ từ frontend đến backend.

#### 1. Trạng thái backend stack

Mở AWS CloudFormation và xác nhận stack `EventApp-Backend-System` đang ở trạng thái **CREATE_COMPLETE**.

![CloudFormation stack hoàn tất](/images/5-Workshop/event-portal/04-cloudformation-complete.png)

#### 2. Backend outputs

Mở tab **Outputs** và xác nhận có các giá trị sau:

- **ApiUrl**
- **UserPoolId**
- **UserPoolClientId**
- **FrontendBucketName**

Các outputs này cho thấy backend resources và frontend bucket đã được tạo thành công.

#### 3. S3 frontend hosting

Mở frontend S3 bucket và kiểm tra:

- Block Public Access đã được tắt cho bucket này.
- Bucket policy cho phép `s3:GetObject` đối với website files.
- Static website hosting đã được bật.
- Bucket website endpoint đã có thể sử dụng.

![Website endpoint](/images/5-Workshop/event-portal/07-copy-website-endpoint.png)

#### 4. Frontend files

Xác nhận toàn bộ file nằm bên trong thư mục `dist` của frontend đã được upload thành công lên root của frontend bucket. Bucket cần có `index.html` ở root để S3 static website endpoint có thể tải ứng dụng đúng cách.

#### Kết quả

Khi các bước kiểm tra hoàn tất, project đã được triển khai với frontend tĩnh trên S3 và serverless backend được tạo bằng CloudFormation.
