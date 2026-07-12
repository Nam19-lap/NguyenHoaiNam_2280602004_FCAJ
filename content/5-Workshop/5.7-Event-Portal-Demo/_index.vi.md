---
title : "Demo luồng User và Admin"
date : 2026-07-12
weight : 7
chapter : false
pre : " <b> 5.7. </b> "
---

#### Mục tiêu của phần demo

Sau khi hoàn thành các bước triển khai backend và frontend trong workshop, phần này ghi lại quá trình chạy thử **AWS Serverless Event Portal** theo hai vai trò chính: **User** và **Admin**. Nội dung demo bắt đầu từ đăng ký/đăng nhập, sau đó đi vào các chức năng quan trọng của hệ thống như xem sự kiện, đăng ký vé, check-in, check-out và theo dõi lịch sử tham dự.

Trong quá trình demo, frontend React/Vite giao tiếp với backend API thông qua các endpoint đã cấu hình. Vì vậy các thao tác như lấy danh sách sự kiện, tạo vé, check-in, check-out và xem lịch sử tham dự không còn là màn hình tĩnh, mà phản ánh dữ liệu được xử lý bởi backend.

#### 1. Vai trò User

User là người tham dự sự kiện. Sau khi đăng ký hoặc đăng nhập, user có thể xem danh sách sự kiện, mở chi tiết từng sự kiện, đăng ký vé và kiểm tra thông tin vé cá nhân.

Các chức năng chính của User gồm:

1. Đăng ký tài khoản hoặc đăng nhập bằng tài khoản đã có.
2. Xem danh sách sự kiện từ backend.
3. Tìm kiếm và lọc sự kiện theo danh mục.
4. Xem chi tiết sự kiện trước khi đăng ký.
5. Đăng ký vé và nhận mã vé/ticket code.
6. Xem lại vé đã đăng ký trong mục **Vé của tôi**.
7. Theo dõi **Lịch sử tham dự** để biết vé nào đã check-in, check-out hoặc còn chờ tham dự.

![User xem lịch sử tham dự](/images/5-Workshop/event-portal-demo/08-user-attendance-history.png)

#### 2. Vai trò Admin

Admin là người vận hành hệ thống sự kiện. Admin sử dụng tài khoản được cấp sẵn để truy cập dashboard quản trị, quản lý sự kiện, xem danh sách thành viên và xử lý check-in/check-out tại cổng sự kiện.

Các chức năng chính của Admin gồm:

1. Đăng nhập bằng tài khoản admin được cấp sẵn.
2. Xem dashboard tổng quan về sự kiện và lượt đăng ký.
3. Thêm, sửa hoặc xóa sự kiện.
4. Xem danh sách thành viên đã đăng ký từng sự kiện.
5. Chọn sự kiện cần vận hành tại màn QR Check-in.
6. Chọn mode **Check-in** hoặc **Check-out** trước khi quét QR/nhập ticket code.
7. Xác nhận trạng thái tham dự và cập nhật dữ liệu về backend.

![Admin QR Check-in và Check-out](/images/5-Workshop/event-portal-demo/09-admin-qr-checkin-checkout-mode.png)

#### 3. Luồng hoạt động tổng quát

Luồng User:

```text
Đăng ký/Đăng nhập -> Xem sự kiện -> Xem chi tiết -> Đăng ký vé -> Xem vé -> Theo dõi lịch sử tham dự
```

Luồng Admin:

```text
Đăng nhập admin -> Mở dashboard -> Quản lý sự kiện -> Xem thành viên -> Check-in -> Check-out
```

Điểm mới của phần demo là hệ thống đã hỗ trợ đủ vòng đời tham dự sự kiện. User không chỉ đăng ký vé, mà còn có thể xem lại lịch sử trạng thái sau khi được admin check-in hoặc check-out. Admin không chỉ điểm danh đầu vào, mà còn có thể xác nhận người tham dự đã rời sự kiện thông qua thao tác check-out.

#### 4. Chia luồng demo theo vai trò

Để dễ theo dõi, phần demo chi tiết được tách thành hai mục nhỏ:

1. [Luồng người dùng User](5.7.1-User-flow/)
2. [Luồng quản trị Admin](5.7.2-Admin-flow/)

Cách tách này giúp giải thích rõ trách nhiệm của từng vai trò. User tập trung vào trải nghiệm tham gia sự kiện, còn Admin tập trung vào quản lý và vận hành tại cổng sự kiện.

#### 5. Kết luận nhanh

Qua phần demo tổng quan, hệ thống đã thể hiện được một luồng hoạt động hoàn chỉnh từ đăng ký/đăng nhập đến xử lý tham dự theo thời gian thực. Các tính năng check-in, check-out và lịch sử tham dự giúp ứng dụng phù hợp hơn với kịch bản vận hành một event portal thực tế.

