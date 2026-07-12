---
title : "Luồng người dùng User"
date : 2026-07-12
weight : 1
chapter : false
pre : " <b> 5.7.1. </b> "
---

#### Mục tiêu của luồng User

Luồng User thể hiện trải nghiệm của một người tham dự sự kiện trên website Event Portal đã được deploy. Người dùng bắt đầu từ trang chủ, đăng ký hoặc đăng nhập tài khoản, xem danh sách sự kiện, mở chi tiết sự kiện và kiểm tra vé đã đăng ký.

#### 1. Đăng ký hoặc đăng nhập

Người tham dự mới có thể chọn **Đăng ký ngay** để tạo tài khoản user. Form đăng ký yêu cầu họ tên, email và mật khẩu. Sau khi tài khoản được tạo, user có thể đăng nhập vào hệ thống và sử dụng các chức năng đăng ký sự kiện.

![Màn hình đăng ký tài khoản](/images/5-Workshop/event-portal-demo/00-register-page.png)

Nếu đã có tài khoản, user dùng màn hình đăng nhập để vào hệ thống.

![Màn hình đăng nhập EventPortal](/images/5-Workshop/event-portal-demo/00-login-page.png)

Sau khi đăng nhập, thanh điều hướng hiển thị thêm mục **Vé của tôi**. Đây là dấu hiệu cho thấy user đã có phiên đăng nhập và có thể truy cập các chức năng cá nhân. Luồng đăng ký này dành cho tài khoản người tham dự; tài khoản Admin sẽ được cấp riêng.

#### 2. Xem danh sách sự kiện

Trang chủ hiển thị toàn bộ sự kiện mà backend trả về. Mỗi event card gồm ảnh bìa, danh mục, thời gian, tên sự kiện, địa điểm, mô tả ngắn và số ghế còn trống.

![Trang danh sách sự kiện](/images/5-Workshop/event-portal-demo/01-homepage-events.png)

Các chức năng người dùng có thể thao tác:

1. **Tìm kiếm**: nhập từ khóa để lọc sự kiện theo tên hoặc mô tả.
2. **Lọc danh mục**: chọn Công nghệ, Âm nhạc hoặc Giáo dục để xem nhóm sự kiện tương ứng.
3. **Xem chi tiết**: nhấn vào event card để mở trang chi tiết sự kiện.
4. **Theo dõi sức chứa**: xem số ghế còn trống trước khi quyết định đăng ký.

Về mặt dữ liệu, frontend gọi API `GET /events`. Nếu có filter danh mục, frontend gọi thêm query string như `GET /events?category=music`.

#### 3. Xem chi tiết sự kiện

Khi user chọn một sự kiện, trang chi tiết hiển thị đầy đủ thông tin của sự kiện đó. Màn hình này giúp người dùng xác nhận thời gian, địa điểm, mô tả và tình trạng chỗ ngồi.

![User xem chi tiết sự kiện và vé](/images/5-Workshop/event-portal-demo/02-user-event-detail-ticket.png)

Các thành phần chính trên trang chi tiết:

- **Ảnh bìa sự kiện**: giúp nhận diện sự kiện nhanh hơn.
- **Tiêu đề và danh mục**: mô tả chủ đề của sự kiện.
- **Thời gian và địa điểm**: thông tin cần thiết để tham gia.
- **Mô tả sự kiện**: giải thích nội dung chính của buổi workshop/event.
- **Trạng thái đặt vé**: hiển thị số ghế đã đăng ký trên tổng số ghế.
- **Ticket card**: nếu user đã đăng ký, hệ thống hiển thị vé điện tử kèm mã vé.

Nếu user chưa đăng ký, khu vực bên phải sẽ hiển thị nút **Đăng ký vé**. Khi nhấn đăng ký, frontend gọi API đăng ký sự kiện. Backend tạo registration record, cập nhật số ghế còn lại và trả về thông tin vé.

#### 4. Kiểm tra vé đã đăng ký

Sau khi đăng nhập, user có thể mở mục **Vé của tôi** để xem lại các vé đang sở hữu.

![User xem danh sách vé đã đăng ký](/images/5-Workshop/event-portal-demo/03-user-my-tickets.png)

Màn hình này có vai trò quan trọng trong trải nghiệm người dùng:

1. Giúp user xác nhận đã đăng ký thành công.
2. Hiển thị mã vé để dùng khi check-in.
3. Cho phép user quay lại trang chi tiết sự kiện khi cần xem thông tin.
4. Là bằng chứng trực quan cho thấy frontend đã lấy được registration data từ backend.

Ở phía backend, danh sách này được lấy từ API liên quan đến user registrations. Dữ liệu registration được liên kết với event metadata để frontend hiển thị tên sự kiện, thời gian, địa điểm và mã vé.

#### 5. Tóm tắt luồng User

Luồng User có thể tóm tắt như sau:

```text
Mở ứng dụng -> Đăng ký/Đăng nhập -> Xem danh sách sự kiện -> Xem chi tiết -> Đăng ký vé -> Xem Vé của tôi
```

Luồng này chứng minh ứng dụng đã hỗ trợ các chức năng cốt lõi cho người tham dự sự kiện: tìm sự kiện, đọc thông tin, đăng ký và quản lý vé cá nhân.
