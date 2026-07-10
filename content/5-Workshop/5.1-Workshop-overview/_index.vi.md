---
title : "Tổng quan workshop"
date : 2026-07-01 
weight : 1 
chapter : false
pre : " <b> 5.1. </b> "
---

#### Triển khai nhanh bằng CloudFormation

Mục tiêu của workshop này là triển khai dự án Event Portal với ít thao tác thủ công hơn bằng cách sử dụng **AWS CloudFormation**. File `template.yaml` trong source code backend mô tả các tài nguyên hạ tầng cần thiết, bao gồm DynamoDB, Cognito, Lambda functions, API Gateway và S3 bucket dành cho frontend.

Với phương pháp này, quy trình triển khai được rút gọn như sau:

1. Đóng gói backend code và upload lên Amazon S3.
2. Cập nhật `template.yaml` để các Lambda functions lấy được backend package từ S3.
3. Upload template lên AWS CloudFormation và tạo backend stack.
4. Copy các thông số Outputs của CloudFormation và cấu hình frontend.
5. Build frontend và upload các file tĩnh đã sinh ra lên frontend S3 bucket.

#### Vì sao dùng Infrastructure as Code?

- Giảm các thao tác thủ công trên AWS Console.
- Giữ kiến trúc AWS nhất quán và có thể triển khai lại.
- Dễ rebuild backend khi cần.
- Hạn chế sai lệch cấu hình giữa môi trường phát triển và triển khai.
- Giúp nhóm tài liệu hóa hạ tầng thực tế ngay trong source code.

#### Kiến trúc hoàn chỉnh

Sau khi hoàn thành, hệ thống gồm frontend tĩnh được host trên S3, REST APIs thông qua API Gateway, backend logic chạy bằng Lambda, dữ liệu lưu trong DynamoDB và xác thực người dùng bằng Cognito.