---
title: "Worklog Tuần 3"
date: 2026-05-11
weight: 3
chapter: false
pre: " <b> 1.3. </b> "
---


### Mục tiêu tuần 3:

* Xây dựng kiến thức vững chắc về các dịch vụ compute của AWS, tập trung vào Amazon EC2 và Auto Scaling.
* Tìm hiểu các giải pháp lưu trữ của AWS và cách triển khai backup, disaster recovery trên cloud.
* Hoàn thành các bài lab hands-on với AWS Backup và AWS Storage Gateway.
* Triển khai static website bằng Amazon S3 và cải thiện khả năng phân phối nội dung với Amazon CloudFront.
* Tìm hiểu các tính năng nâng cao của Amazon S3 phục vụ bảo vệ dữ liệu và replication.

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 2 | **Module 3: Nền tảng Compute & Storage** <br> - Tìm hiểu kiến trúc và các tính năng của Amazon EC2, bao gồm instance types, AMIs, EBS volumes, User Data và Instance Metadata. <br> - Tìm hiểu các khái niệm cơ bản về Auto Scaling, Amazon EFS và Amazon Lightsail. | 11/05/2026 | 11/05/2026 | [M3-01](https://youtu.be/-t5h4N6vfBs), [M3-01-01](https://youtu.be/e7XeKdOVq40), [M3-01-02](https://youtu.be/yAR6QRT3N1k), [M3-01-03](https://youtu.be/hKr_TfGP7NY), [M3-01-04](https://youtu.be/6IHNDJ85aoQ), [M3-01-05](https://youtu.be/_v_43Wi7zjo), [M3-01-06](https://youtu.be/Ew3QRaKJQSA), [M3-01-07](https://youtu.be/bbLcPitXJSY), [M3-02](https://youtu.be/hFVYG8WqfU0) |
| 3 | **Lab 13: AWS Backup** <br> - Cấu hình môi trường cần thiết và tạo backup plan tự động. <br> - Thực hiện kiểm thử khôi phục dữ liệu và xóa tài nguyên lab sau khi hoàn thành. | 12/05/2026 | 12/05/2026 | [Lab13-01](https://youtu.be/7r_-MnOO64s), [Lab13-02.2](https://youtu.be/OBWLgMUiy9s), [Lab13-03](https://youtu.be/-1ivCChsGFo), [Lab13-05](https://youtu.be/nd-o5GP6tXg), [Lab13-06](https://youtu.be/TvQSnXUGxP8) |
| 4 | **Lab 24: AWS Storage Gateway** <br> - Tạo Amazon S3 bucket và EC2 instance theo yêu cầu của bài lab. <br> - Cấu hình Storage Gateway và File Shares để hiểu cách tích hợp lưu trữ hybrid cloud. | 13/05/2026 | 13/05/2026 | [Lab24-01.1](https://youtu.be/3vSrTeWroSs), [Lab24-01.2](https://youtu.be/xVrhpe8OpVU), [Lab24-02.1](https://youtu.be/Je2jPk7HhLQ), [Lab24-02.2](https://youtu.be/3Zp9GSMO-VI) |
| 5 | **Lab 57 - Phần 1: Static Website Hosting** <br> - Tạo Amazon S3 bucket và bật tính năng static website hosting. <br> - Cấu hình public access, triển khai website và tăng tốc phân phối nội dung bằng Amazon CloudFront. | 14/05/2026 | 14/05/2026 | [Lab57-02.1](https://youtu.be/7kmhQLYkrnI), [Lab57-02.2](https://youtu.be/9yUYIrq05Vc), [Lab57-03](https://youtu.be/9Cd_dAUCh9o), [Lab57-04](https://youtu.be/iw0qEi-PiOc), [Lab57-05](https://youtu.be/pJEhAwGyu9g), [Lab57-06](https://youtu.be/N2IGbJnY3eo), [Lab57-07.1](https://youtu.be/O6F1UPNyWNI), [Lab57-07.2](https://youtu.be/5RxYavHbgVE), [Lab57-07.3](https://youtu.be/TicCP8LfNPU) |
| 6 | **Lab 57 - Phần 2: Tính năng nâng cao của Amazon S3** <br> - Thực hành Versioning, Object Move và Cross-Region Replication. <br> - Xóa toàn bộ tài nguyên tạm thời và tổng kết các kiến thức chính trong tuần. | 15/05/2026 | 15/05/2026 | [Lab57-08](https://youtu.be/HcLBLpYHtCw), [Lab57-09](https://youtu.be/QQFf3nlCJVY), [Lab57-10](https://youtu.be/rSSZOhZnoHk), [Lab57-11](https://youtu.be/vvFaLmtNtEM) |


### Kết quả đạt được tuần 3:

* Nắm được kiến thức thực tế về Amazon EC2 thông qua việc tìm hiểu cách instances, AMIs, EBS volumes, User Data và Metadata hoạt động cùng nhau trong AWS.
* Hiểu rõ hơn về Auto Scaling và vai trò của dịch vụ này trong việc cải thiện tính sẵn sàng của ứng dụng và tối ưu sử dụng tài nguyên.
* Tạo thành công backup plan, thực hiện thao tác restore và hiểu tầm quan trọng của bảo vệ dữ liệu tự động với AWS Backup.
* Biết cách AWS Storage Gateway kết nối môi trường on-premises với các dịch vụ lưu trữ AWS thông qua kiến trúc hybrid cloud.
* Xuất bản static website trên Amazon S3 và cải thiện khả năng truy cập, hiệu năng bằng Amazon CloudFront.
* Tìm hiểu các khả năng nâng cao của Amazon S3 như Versioning và Cross-Region Replication để tăng độ bền và tính sẵn sàng của dữ liệu.
* Tuân thủ best practices về quản lý chi phí AWS bằng cách xóa toàn bộ tài nguyên lab sau khi hoàn thành từng bài thực hành.


