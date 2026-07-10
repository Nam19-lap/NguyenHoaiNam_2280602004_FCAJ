---
title: "Worklog Tuần 9"
date: 2026-06-15
weight: 9
chapter: false
pre: " <b> 1.9. </b> "
---


### Mục tiêu tuần 9:

* Có kinh nghiệm thực hành trong việc triển khai và quản trị Amazon RDS.
* Xây dựng môi trường networking an toàn cho các dịch vụ database trên AWS.
* Triển khai ứng dụng kết nối đến Amazon RDS database.
* Tìm hiểu AWS Database Migration Service (DMS) và quy trình migration database.
* Hiểu các thách thức phổ biến khi migrate database lên AWS.

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 2 | **Lab 05 - Phần 1: Network Infrastructure** <br> - Tạo Virtual Private Cloud (VPC) và database subnet groups. <br> - Cấu hình Security Groups cho Amazon EC2 và Amazon RDS instances. <br> - Khởi tạo EC2 instance để hỗ trợ môi trường database. | 15/06/2026 | 15/06/2026 | [Lab 05-2.1](https://www.youtube.com/watch?v=B5rOeWQWg1c) <br> [Lab 05-2.2](https://www.youtube.com/watch?v=VSKRP7BFsoQ) <br> [Lab 05-2.3](https://www.youtube.com/watch?v=oMjPdSmU4co) <br> [Lab 05-2.4](https://www.youtube.com/watch?v=OWjX0FsbX9E) <br> [Lab 05-3](https://www.youtube.com/watch?v=NZZRBfCJ2AY) |
| 3 | **Lab 05 - Phần 2: Triển khai Amazon RDS** <br> - Tạo Amazon RDS database instance. <br> - Kết nối ứng dụng đến database. <br> - Thực hành backup database, restore và cleanup tài nguyên. | 16/06/2026 | 16/06/2026 | [Lab 05-4](https://www.youtube.com/watch?v=SlP-KdSs3IM) <br> [Lab 05-5](https://www.youtube.com/watch?v=P_dyDq7rp1A) <br> [Lab 05-6](https://www.youtube.com/watch?v=7So4xNZJ6bk) <br> [Lab 05-7](https://www.youtube.com/watch?v=0WiTedZTcpQ) |
| 4 | **Lab 43 - Database Migration (Phần 1)** <br> - Kết nối đến EC2 bằng Remote Desktop và Fleet Manager. <br> - Cấu hình source databases và chuẩn bị migration settings cho Amazon Aurora MySQL. | 17/06/2026 | 17/06/2026 | [Lab 43-01](https://www.youtube.com/watch?v=cxwAOP1379s) đến [Lab 43-08](https://www.youtube.com/watch?v=bTWkX3xHN4s) |
| 5 | **Lab 43 - Database Migration (Phần 2)** <br> - Thực hiện schema conversion và cấu hình migration endpoints. <br> - Tạo migration tasks, giám sát quá trình chạy và xem migration logs. <br> - Tìm hiểu các lỗi migration phổ biến và kỹ thuật troubleshooting. | 18/06/2026 | 18/06/2026 | [Lab 43-09](https://www.youtube.com/watch?v=s-6mXTFXwG8) đến [Lab 43-17](https://www.youtube.com/watch?v=MU8XHe3OoxQ) |
| 6 | **Ôn tập tuần** <br> - Ôn lại quy trình triển khai database và database migration. <br> - Xóa tài nguyên AWS tạm thời và tổng kết các kiến thức chính đã học trong tuần. | 19/06/2026 | 19/06/2026 | |


### Kết quả đạt được tuần 9:

* Triển khai thành công Amazon RDS database trong môi trường networking an toàn trên AWS.
* Cải thiện kỹ năng thực hành trong việc cấu hình VPC, subnet groups và Security Groups cho database services.
* Kết nối ứng dụng đến Amazon RDS và thực hành backup, recovery, cùng các tác vụ quản trị database cơ bản.
* Nắm được quy trình đầy đủ khi migrate database bằng AWS Database Migration Service (DMS) và Amazon Aurora.
* Có kinh nghiệm giám sát migration tasks, xác thực dữ liệu đã migrate và xử lý các lỗi migration phổ biến.
* Củng cố kiến thức tổng quan về AWS database services và tuân thủ best practices bằng cách xóa toàn bộ tài nguyên lab sau khi hoàn thành bài thực hành.


