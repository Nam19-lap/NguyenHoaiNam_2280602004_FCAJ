---
title : "Chuẩn bị backend code"
date : 2026-07-01 
weight : 2 
chapter : false
pre : " <b> 5.2. </b> "
---

#### Mục đích

Ở bước này, ta đóng gói source code backend và upload lên Amazon S3. Sau đó CloudFormation sẽ sử dụng package này để tự động tạo các Lambda functions.

#### 1. Build backend code ở local

1. Mở Terminal hoặc Command Prompt.
2. Di chuyển vào thư mục backend:

```bash
cd "C:\Users\Sieu chu nhiem\Desktop\aws-serverless-event-portal\backend"
```

3. Cài đặt dependencies:

```bash
npm install
```

4. Build source code TypeScript sang JavaScript:

```bash
npm run build
```

5. Sau khi build xong, thư mục backend sẽ sinh ra thư mục `dist`.
6. Copy `package.json` và `node_modules` vào trong thư mục `dist`.
7. Nén toàn bộ file bên trong `dist` thành Lambda deployment package tên `backend-code.zip`.

#### 2. Tạo S3 bucket để chứa backend package

Mở Amazon S3 console và tạo bucket ở Region **Asia Pacific (Singapore) ap-southeast-1**. Trong workshop này, backend package được upload vào một bucket tạm tên `eventapp-backend-package-ap-southeast-1`.

#### 3. Upload backend package

Mở bucket, chọn **Upload**, chọn package `backend-code.zip` và upload lên S3.

#### 4. Copy S3 URI

Sau khi upload thành công, mở object vừa upload và copy **S3 URI**. Giá trị này sẽ được dùng cho các dòng Lambda `CodeUri` trong file `template.yaml`.

Ví dụ S3 URI:

```text
s3://eventapp-backend-package-ap-southeast-1/backend-code.zip
```

Sau bước này, cần lưu lại S3 URI của backend package để dùng ở bước triển khai CloudFormation.
