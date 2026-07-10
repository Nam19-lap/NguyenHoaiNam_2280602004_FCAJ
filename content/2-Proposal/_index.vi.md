---
title: "Bản đề xuất"
date: 2024-01-01
weight: 2
chapter: false
pre: " <b> 2. </b> "
---

# Đề Xuất Dự Án AWS Serverless Event Portal

**Tên dự án:** AWS Serverless Event Portal  
**Nhóm:** Hiếu An  
**Loại dự án:** Ứng dụng quản lý sự kiện cloud-native

## 1. Tóm Tắt Dự Án

**AWS Serverless Event Portal** là một ứng dụng web cloud-native được xây dựng nhằm đơn giản hóa quá trình tổ chức và tham gia sự kiện bằng các dịch vụ AWS Serverless. Hệ thống cung cấp một nền tảng tập trung để người dùng có thể xem danh sách sự kiện, đăng ký trực tuyến, nhận vé điện tử, check-in bằng mã QR, gửi phản hồi và xem các gợi ý sự kiện phù hợp. Đồng thời, quản trị viên có thể quản lý sự kiện, người tham gia, lượt đăng ký và dữ liệu điểm danh thông qua một giao diện web bảo mật.

Thay vì sử dụng mô hình máy chủ truyền thống, dự án tận dụng các dịch vụ được quản lý của AWS để cải thiện khả năng mở rộng, tính sẵn sàng và hiệu quả vận hành. Frontend được host bằng **Amazon S3** và phân phối qua **Amazon CloudFront**. Backend API được cung cấp thông qua **Amazon API Gateway** và xử lý bằng **AWS Lambda**. **Amazon Cognito** đảm nhiệm xác thực và phân quyền người dùng, trong khi **Amazon DynamoDB** lưu trữ dữ liệu sự kiện, lượt đăng ký, vé, lịch sử check-in và phản hồi. Log, metric, cảnh báo và thông báo vận hành được quản lý thông qua **Amazon CloudWatch** và **Amazon SNS**.

Dự án vừa là một bài thực hành ứng dụng trong môi trường đại học, vừa là minh chứng cho cách phát triển ứng dụng hiện đại bằng kiến trúc AWS Serverless. Nhờ sử dụng các dịch vụ managed cloud, hệ thống giảm đáng kể công việc quản trị hạ tầng và tạo nền tảng có thể mở rộng trong tương lai.

## 2. Vấn Đề Cần Giải Quyết

### Vấn đề hiện tại

Nhiều trường đại học, câu lạc bộ sinh viên và đơn vị tổ chức sự kiện quy mô nhỏ vẫn quản lý sự kiện bằng các công cụ thủ công hoặc bán thủ công như bảng tính, ứng dụng nhắn tin và biểu mẫu trực tuyến. Cách làm này có thể phù hợp với các hoạt động nhỏ, nhưng nhanh chóng trở nên kém hiệu quả khi số lượng sự kiện hoặc người tham gia tăng lên.

Một số vấn đề thường gặp gồm dữ liệu đăng ký bị trùng lặp, quá trình điểm danh chậm, khó theo dõi số lượng người tham gia, thiếu cái nhìn tổng quan về dữ liệu người dùng và mất nhiều thời gian để tổng hợp báo cáo. Người tham gia cũng chưa có một nền tảng tập trung để tìm kiếm sự kiện sắp diễn ra, quản lý đăng ký hoặc truy cập vé điện tử.

Nếu không có một hệ thống quản lý tích hợp, ban tổ chức phải tốn nhiều công sức để duy trì dữ liệu sự kiện, kiểm tra điểm danh, quản lý danh sách chờ và thu thập phản hồi sau sự kiện.

### Giải pháp đề xuất

**AWS Serverless Event Portal** giải quyết các vấn đề trên bằng cách cung cấp một nền tảng quản lý sự kiện tích hợp trên nền tảng cloud.

Người dùng truy cập ứng dụng web thông qua trình duyệt. Frontend giao tiếp với backend API thông qua Amazon API Gateway. API Gateway gọi các AWS Lambda function để xử lý logic chính của hệ thống, bao gồm tạo sự kiện, đăng ký sự kiện, check-in bằng mã QR, gợi ý sự kiện, xử lý phản hồi và các thao tác quản trị.

Amazon Cognito bảo mật quá trình đăng nhập và kiểm soát quyền truy cập. Amazon DynamoDB lưu trữ dữ liệu ứng dụng với độ sẵn sàng cao và độ trễ thấp. Amazon CloudWatch thu thập log và metric, trong khi Amazon SNS có thể gửi thông báo khi CloudWatch alarm được kích hoạt.

Hệ thống dự kiến hỗ trợ các chức năng chính sau:

- Xác thực và phân quyền người dùng
- Xem và tìm kiếm sự kiện
- Đăng ký sự kiện trực tuyến
- Quản lý vé điện tử
- Check-in bằng mã QR
- Quản lý danh sách chờ
- Gợi ý sự kiện
- Quản lý phản hồi và đánh giá
- Trang quản trị dành cho ban tổ chức

### Lợi ích và giá trị mang lại

Hệ thống giúp giảm công việc thủ công bằng cách tập trung hóa quá trình đăng ký sự kiện, quản lý người tham gia, phát hành vé và theo dõi điểm danh. Ban tổ chức có thể quản lý thông tin sự kiện trên một nền tảng duy nhất thay vì sử dụng nhiều công cụ rời rạc.

Về mặt kỹ thuật, các dịch vụ AWS Serverless giúp giảm nhu cầu quản lý máy chủ, hệ điều hành và chính sách mở rộng thủ công. Các dịch vụ như AWS Lambda, Amazon DynamoDB và Amazon API Gateway có thể mở rộng theo nhu cầu thực tế, phù hợp với mô hình sự kiện của sinh viên, workshop và các hệ thống quản lý sự kiện quy mô nhỏ đến trung bình.

Giải pháp cũng có giá trị lâu dài vì kiến trúc module có thể được mở rộng thêm các tính năng như gợi ý nâng cao, dashboard phân tích, nhắc lịch qua email hoặc tích hợp AI hỗ trợ quản lý sự kiện.

## 3. Kiến Trúc Giải Pháp

AWS Serverless Event Portal sử dụng kiến trúc serverless, tách riêng các thành phần gồm phân phối frontend, xác thực, xử lý API, logic nghiệp vụ, lưu trữ dữ liệu và giám sát vận hành thành các dịch vụ managed độc lập. Cách thiết kế này giúp hệ thống dễ bảo trì hơn và từng thành phần có thể mở rộng theo tải riêng của nó.

Frontend được host trên Amazon S3 và phân phối đến người dùng thông qua Amazon CloudFront. Amazon Cognito xử lý xác thực người dùng. Sau khi đăng nhập, frontend gửi request đã xác thực đến Amazon API Gateway. API Gateway xác thực và định tuyến request đến các AWS Lambda function tương ứng. Lambda xử lý logic ứng dụng và đọc/ghi dữ liệu trong Amazon DynamoDB. Log và metric vận hành được thu thập bằng Amazon CloudWatch, còn các cảnh báo quan trọng có thể gửi thông báo cho quản trị viên thông qua Amazon SNS.

![Kiến trúc AWS Serverless Event Portal](/images/2-Proposal/serverless-event-portal-architecture.png)

### Các Dịch Vụ AWS Sử Dụng

| Dịch vụ AWS | Mục đích sử dụng |
| --- | --- |
| Amazon S3 | Host ứng dụng frontend React và static assets. |
| Amazon CloudFront | Phân phối nội dung frontend với độ trễ thấp hơn. |
| Amazon Cognito | Cung cấp xác thực và phân quyền người dùng. |
| Amazon API Gateway | Cung cấp REST API để frontend giao tiếp với backend. |
| AWS Lambda | Thực thi logic backend của ứng dụng. |
| Amazon DynamoDB | Lưu sự kiện, người dùng, lượt đăng ký, vé, phản hồi và dữ liệu check-in. |
| Amazon CloudWatch | Thu thập log, metric và alarm. |
| Amazon SNS | Gửi thông báo vận hành khi alarm được kích hoạt. |
| AWS SAM / CloudFormation | Triển khai và quản lý hạ tầng serverless. |

### Thiết Kế Thành Phần

**Lớp Frontend**  
Người dùng truy cập Event Portal thông qua Amazon CloudFront. CloudFront phân phối frontend React được host trên Amazon S3, giúp cải thiện tốc độ tải trang và tính sẵn sàng.

**Lớp Xác Thực**  
Amazon Cognito quản lý đăng nhập và phân quyền người dùng. JWT token do Cognito cấp được dùng để bảo vệ các API request.

**Lớp API**  
Amazon API Gateway đóng vai trò là điểm vào bảo mật cho các request từ frontend và chuyển request đến đúng Lambda function.

**Lớp Logic Nghiệp Vụ**  
AWS Lambda chứa logic chính của ứng dụng, bao gồm quản lý sự kiện, xử lý đăng ký, check-in bằng mã QR, xử lý gợi ý sự kiện, xử lý phản hồi và các thao tác quản trị.

**Lớp Dữ Liệu**  
Amazon DynamoDB lưu trữ dữ liệu ứng dụng như hồ sơ người dùng, thông tin sự kiện, lượt đăng ký, vé điện tử, lịch sử check-in, phản hồi và thông báo.

**Lớp Giám Sát**  
Amazon CloudWatch giám sát quá trình thực thi Lambda, hoạt động API, log và metric. CloudWatch alarm có thể kích hoạt Amazon SNS để gửi thông báo khi xuất hiện tình trạng bất thường.

## 4. Triển Khai Kỹ Thuật

### Các Giai Đoạn Triển Khai

Dự án được lập kế hoạch và phát triển qua bốn giai đoạn chính.

| Giai đoạn | Nội dung chính |
| --- | --- |
| Giai đoạn 1 - Phân tích yêu cầu và thiết kế kiến trúc | Phân tích yêu cầu hệ thống, xác định dịch vụ AWS phù hợp, thiết kế kiến trúc serverless, chuẩn bị schema cơ sở dữ liệu và luồng hoạt động của ứng dụng. |
| Giai đoạn 2 - Phát triển backend | Phát triển AWS Lambda functions, cấu hình Amazon API Gateway, tích hợp Amazon Cognito, triển khai bảng Amazon DynamoDB và xây dựng backend APIs. |
| Giai đoạn 3 - Phát triển frontend | Xây dựng frontend bằng React và Vite, tạo giao diện xem sự kiện, đăng ký, vé, QR check-in, phản hồi và quản trị. |
| Giai đoạn 4 - Tích hợp, kiểm thử và triển khai | Tích hợp frontend và backend, kiểm thử các chức năng chính, triển khai serverless resources bằng AWS SAM và CloudFormation, host frontend bằng Amazon S3 và CloudFront. |

### Yêu Cầu Kỹ Thuật

**Môi trường phát triển**

- Node.js
- React + Vite
- TypeScript
- GitHub
- Visual Studio Code

**Dịch vụ AWS**

- Amazon S3
- Amazon CloudFront
- Amazon Cognito
- Amazon API Gateway
- AWS Lambda
- Amazon DynamoDB
- Amazon CloudWatch
- Amazon SNS
- AWS SAM
- AWS CloudFormation

### Tính Năng Ứng Dụng

Hệ thống hoàn chỉnh dự kiến hỗ trợ:

- Xác thực người dùng
- Xem danh sách sự kiện
- Đăng ký sự kiện
- Quản lý vé điện tử
- Check-in bằng mã QR
- Quản lý danh sách chờ
- Gợi ý sự kiện
- Phản hồi và đánh giá
- Dashboard quản trị
- Giám sát và ghi log trên cloud

## 5. Timeline & Milestones

### Timeline Dự Án

Dự án AWS Serverless Event Portal được lên kế hoạch hoàn thành trong khoảng hai tháng. Quá trình phát triển được chia thành bốn giai đoạn chính để đảm bảo việc triển khai, kiểm thử và hoàn thiện diễn ra có hệ thống.

| Giai đoạn | Thời gian | Hoạt động |
| --- | --- | --- |
| Giai đoạn 1 - Lập kế hoạch và thiết kế kiến trúc | Tuần 1-2 | Phân tích yêu cầu, xác định dịch vụ AWS, thiết kế kiến trúc serverless, database schema và luồng hoạt động của ứng dụng. |
| Giai đoạn 2 - Phát triển backend | Tuần 3-4 | Phát triển Lambda functions, cấu hình API Gateway, tích hợp Cognito, triển khai DynamoDB và xây dựng backend APIs. |
| Giai đoạn 3 - Phát triển frontend và tích hợp | Tuần 5-6 | Phát triển frontend React, tích hợp backend APIs, triển khai tính năng đăng ký, QR check-in, gợi ý sự kiện và xác thực. |
| Giai đoạn 4 - Kiểm thử và triển khai | Tuần 7-8 | Kiểm thử hệ thống, sửa lỗi, triển khai serverless resources bằng AWS SAM và CloudFormation, deploy frontend lên S3 và CloudFront, chuẩn bị demo cuối cùng. |

### Các Mốc Quan Trọng

- Hoàn thành thiết kế kiến trúc AWS
- Hoàn thành backend API
- Tích hợp frontend
- Xác thực người dùng bằng Amazon Cognito
- Hoàn thành QR Code Check-in
- Hoàn thành deployment trên AWS
- Kiểm thử hệ thống cuối cùng
- Trình bày workshop và demo dự án

## 6. Ước Tính Ngân Sách

AWS Serverless Event Portal được phát triển chủ yếu như một dự án học thuật và demo workshop. Vì hệ thống chưa hướng đến lưu lượng production ở giai đoạn này, chi phí vận hành dự kiến ở mức thấp.

Chi phí vận hành chi tiết có thể được đánh giá trong giai đoạn triển khai bằng **AWS Pricing Calculator**. Việc ước tính cần xem xét mức sử dụng hằng tháng của các dịch vụ sau:

- Amazon S3 storage và request
- Amazon CloudFront data transfer
- Amazon API Gateway requests
- AWS Lambda invocations
- Amazon DynamoDB storage và read/write requests
- Amazon Cognito Monthly Active Users (MAU)
- Amazon CloudWatch logs và monitoring
- Amazon SNS notification delivery

Do kiến trúc sử dụng mô hình serverless pay-as-you-go, tài nguyên được tính phí dựa trên mức sử dụng thực tế thay vì phải duy trì máy chủ chạy liên tục. Điều này làm cho giải pháp phù hợp với dự án sinh viên, sự kiện trong trường đại học và hệ thống quản lý sự kiện quy mô nhỏ đến trung bình.

## 7. Đánh Giá Rủi Ro

### Ma Trận Rủi Ro

| Rủi ro | Xác suất | Mức ảnh hưởng |
| --- | --- | --- |
| Lỗi cấu hình dịch vụ AWS | Trung bình | Cao |
| Lỗi xác thực người dùng | Thấp | Cao |
| Lỗi API hoặc Lambda execution | Trung bình | Cao |
| Dữ liệu DynamoDB không nhất quán | Thấp | Trung bình |
| Vấn đề khi quét mã QR | Trung bình | Trung bình |
| Chi phí AWS phát sinh ngoài dự kiến | Thấp | Trung bình |

### Chiến Lược Giảm Thiểu

**Cấu hình AWS**  
Các tài nguyên AWS nên được triển khai bằng AWS SAM và CloudFormation để cấu hình hạ tầng nhất quán và dễ tái tạo.

**Xác thực**  
Amazon Cognito cung cấp xác thực và phân quyền an toàn bằng JWT token, giúp giảm rủi ro truy cập trái phép vào các API được bảo vệ.

**Giám sát**  
Amazon CloudWatch giám sát quá trình thực thi Lambda, log ứng dụng và metric vận hành. CloudWatch alarm có thể thông báo cho quản trị viên thông qua Amazon SNS khi phát hiện hành vi bất thường.

**Độ tin cậy dữ liệu**  
Amazon DynamoDB cung cấp khả năng lưu trữ NoSQL có tính sẵn sàng và độ bền cao, đồng thời hỗ trợ tự động mở rộng để giảm gánh nặng quản trị cơ sở dữ liệu.

**QR Code Check-in**  
Ứng dụng hỗ trợ quét mã QR thông qua camera trình duyệt. Trong trường hợp không truy cập được camera, người dùng có thể nhập mã vé thủ công như phương án thay thế.

### Kế Hoạch Dự Phòng

Nếu gặp sự cố deployment trong buổi demo, dự án vẫn có thể được trình bày bằng môi trường local và mock services. Cách này đảm bảo các chức năng cốt lõi như xem sự kiện, đăng ký, QR check-in và quản trị vẫn có thể được demo.

## 8. Kết Quả Kỳ Vọng

### Kết Quả Kỹ Thuật

Khi hoàn thành, AWS Serverless Event Portal dự kiến cung cấp:

- Một nền tảng quản lý sự kiện serverless hoạt động được
- Xác thực người dùng an toàn bằng Amazon Cognito
- Đăng ký sự kiện trực tuyến và quản lý người tham gia
- Tạo vé điện tử và QR Code Check-in
- Chức năng gợi ý sự kiện
- Dashboard quản trị sự kiện
- Giám sát và thông báo vận hành trên cloud
- Backend có khả năng mở rộng bằng AWS Lambda và Amazon DynamoDB

### Kết Quả Học Tập

Dự án mang lại kinh nghiệm thực tế trong việc thiết kế và triển khai ứng dụng cloud-native bằng công nghệ AWS Serverless. Thành viên trong nhóm có cơ hội thực hành với:

- AWS Serverless Architecture
- Infrastructure as Code bằng AWS SAM và CloudFormation
- Phát triển REST API với Amazon API Gateway
- Phát triển backend serverless bằng AWS Lambda
- Thiết kế NoSQL database với Amazon DynamoDB
- Xác thực người dùng bằng Amazon Cognito
- Giám sát cloud bằng Amazon CloudWatch
- Triển khai frontend bằng Amazon S3 và Amazon CloudFront

### Giá Trị Dài Hạn

AWS Serverless Event Portal có thể trở thành nền tảng tái sử dụng cho các ứng dụng quản lý sự kiện và dự án cloud computing trong tương lai. Kiến trúc serverless dạng module cho phép tích hợp thêm tính năng hoặc dịch vụ AWS mới mà không cần thay đổi quá nhiều về kiến trúc. Dự án cũng thể hiện quy trình phát triển ứng dụng cloud hiện đại và có thể mở rộng để hỗ trợ quy mô lớn hơn hoặc các ý tưởng tích hợp AI hỗ trợ sự kiện trong tương lai.