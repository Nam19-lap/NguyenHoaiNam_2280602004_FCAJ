---
title : "Luồng quản trị Admin"
date : 2026-07-12
weight : 2
chapter : false
pre : " <b> 5.7.2. </b> "
---

#### Mục tiêu của luồng Admin

Luồng Admin thể hiện vai trò của người vận hành hệ thống sự kiện. Admin không chỉ xem dữ liệu như user mà còn có quyền quản lý sự kiện, theo dõi lượt đăng ký, xem danh sách thành viên và xử lý check-in/check-out tại cổng sự kiện.

Admin không tự tạo tài khoản thông qua form đăng ký công khai. Tài khoản admin được chuẩn bị và cấp sẵn để đảm bảo chỉ người có quyền mới truy cập chức năng quản trị.

#### 1. Đăng nhập với vai trò Admin

Admin đăng nhập qua cùng màn hình đăng nhập với user, nhưng sử dụng tài khoản admin đã được cấp. Sau khi đăng nhập thành công, hệ thống nhận diện vai trò quản trị và thanh điều hướng xuất hiện thêm các mục dành cho admin.

![Màn hình đăng nhập EventPortal](/images/5-Workshop/event-portal-demo/00-login-page.png)

Sau bước này, admin có thể truy cập:

- **Quản trị**: xem dashboard và quản lý sự kiện.
- **Check-in**: mở màn hình vận hành QR để check-in/check-out.
- **Hồ sơ**: xem thông tin tài khoản đang đăng nhập.

#### 2. Dashboard quản trị

Dashboard là màn hình chính của admin. Màn hình này tổng hợp số lượng sự kiện, tổng lượt đặt vé và tỉ lệ lấp đầy trung bình.

![Admin dashboard](/images/5-Workshop/event-portal-demo/04-admin-dashboard.png)

Các phần chính:

1. **Metric cards**: hiển thị tổng sự kiện, tổng đặt vé và tỉ lệ lấp đầy.
2. **Bảng sự kiện**: liệt kê ảnh, tiêu đề, danh mục, thời gian, địa điểm và số vé đã đặt.
3. **Nút Thành viên**: mở danh sách user đã đăng ký từng sự kiện.
4. **Nút Sửa**: mở form chỉnh sửa thông tin sự kiện.
5. **Nút Xóa**: xóa sự kiện khỏi hệ thống nếu cần.
6. **Mở QR Check-in**: chuyển sang màn hình vận hành tại cổng.

#### 3. Thêm hoặc chỉnh sửa sự kiện

Khi chọn **Thêm sự kiện mới**, hệ thống mở modal nhập thông tin sự kiện. Form này cho phép admin nhập tiêu đề, danh mục, tổng số ghế, thời gian, địa điểm, URL ảnh bìa và mô tả.

![Admin tạo sự kiện mới](/images/5-Workshop/event-portal-demo/06-admin-create-event-modal.png)

Luồng xử lý:

1. Admin nhập dữ liệu vào form.
2. Frontend kiểm tra các trường bắt buộc.
3. Frontend gửi request tạo/cập nhật sự kiện đến backend.
4. Backend lưu event metadata.
5. Sau khi lưu thành công, danh sách sự kiện được refresh.

#### 4. Xem danh sách thành viên của sự kiện

Từ dashboard, admin có thể chọn **Thành viên** để xem danh sách người đã đăng ký một sự kiện cụ thể.

![Admin xem danh sách thành viên](/images/5-Workshop/event-portal-demo/05-admin-members.png)

Màn hình thành viên hỗ trợ:

- Kiểm tra user nào đã đăng ký sự kiện.
- Đối chiếu mã vé trước khi check-in/check-out.
- Theo dõi trạng thái người tham dự.
- Chuẩn bị danh sách vận hành tại cổng sự kiện.

#### 5. QR Check-in và Check-out

Màn hình **QR Check-in** là nơi admin vận hành trạng thái tham dự tại cổng sự kiện. Sau khi cập nhật tính năng mới, màn hình này có thêm mode **Check-in / Check-out** để admin chủ động chọn hành động trước khi quét QR hoặc nhập ticket code.

![Admin QR Check-in và Check-out](/images/5-Workshop/event-portal-demo/09-admin-qr-checkin-checkout-mode.png)



Các thành phần chính sau khi cập nhật:

1. **Dropdown sự kiện**: chọn sự kiện cần vận hành.
2. **Chế độ quét**: chọn **Check-in** hoặc **Check-out**.
3. **Khu vực camera/QR**: bật camera để quét mã vé thật.
4. **Mã vé / QR payload**: nhập ticket code thủ công nếu không dùng camera.
5. **Danh sách vé tham dự**: hiển thị các vé đã đăng ký của sự kiện được chọn.
6. **Trạng thái vé**: cho biết vé chưa check-in, đã check-in chờ check-out hoặc đã check-out.
7. **Phiên vừa xử lý**: ghi lại các thao tác admin vừa thực hiện trong phiên hiện tại.

#### 6. Tóm tắt luồng Admin

Luồng Admin có thể tóm tắt như sau:

```text
Đăng nhập admin -> Mở dashboard -> Quản lý sự kiện -> Xem thành viên -> Chọn mode Check-in/Check-out -> Quét QR hoặc nhập mã vé -> Cập nhật trạng thái tham dự
```

Luồng này chứng minh hệ thống đã có các chức năng vận hành cốt lõi cho ban tổ chức sự kiện: theo dõi dữ liệu, quản lý sự kiện, kiểm tra danh sách người tham gia, xác nhận người vào sự kiện và xác nhận người rời sự kiện.

