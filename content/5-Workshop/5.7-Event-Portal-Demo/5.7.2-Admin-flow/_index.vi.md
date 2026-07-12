---
title : "Luồng quản trị Admin"
date : 2026-07-12
weight : 2
chapter : false
pre : " <b> 5.7.2. </b> "
---

#### Mục tiêu của luồng Admin

Luồng Admin thể hiện vai trò của người vận hành hệ thống sự kiện trên website Event Portal đã deploy. Admin không chỉ xem dữ liệu như user mà còn có quyền quản lý sự kiện, theo dõi lượt đăng ký, xem danh sách thành viên và hỗ trợ check-in.

Admin không tự tạo tài khoản thông qua form đăng ký công khai. Thay vào đó, tài khoản admin sẽ được chuẩn bị và cấp sẵn để đảm bảo chỉ người có quyền mới truy cập được các chức năng quản trị.

#### 1. Đăng nhập với vai trò Admin

Admin đăng nhập qua cùng màn hình đăng nhập với user, nhưng sử dụng thông tin tài khoản admin đã được cấp. Sau khi đăng nhập thành công, hệ thống nhận diện vai trò quản trị và thanh điều hướng xuất hiện thêm các mục dành cho admin.

![Màn hình đăng nhập EventPortal](/images/5-Workshop/event-portal-demo/00-login-page.png)

Sau bước này, admin có thể truy cập:

- **Quản trị**: xem dashboard và quản lý sự kiện.
- **Check-in**: mô phỏng quét QR/ticket code để điểm danh.
- **Hồ sơ**: xem thông tin tài khoản đang đăng nhập.

#### 2. Dashboard quản trị

Dashboard là màn hình chính của admin. Màn hình này tổng hợp số lượng sự kiện, tổng lượt đặt vé và tỉ lệ lấp đầy trung bình.

![Admin dashboard](/images/5-Workshop/event-portal-demo/04-admin-dashboard.png)

Các phần chính của dashboard:

1. **Metric cards**: hiển thị tổng sự kiện, tổng đặt vé và tỉ lệ lấp đầy.
2. **Bảng sự kiện**: liệt kê ảnh, tiêu đề, danh mục, thời gian, địa điểm và số vé đã đặt.
3. **Nút Thành viên**: mở danh sách user đã đăng ký từng sự kiện.
4. **Nút Sửa**: mở form chỉnh sửa thông tin sự kiện.
5. **Nút Xóa**: xóa sự kiện khỏi hệ thống nếu cần.
6. **Mở QR Check-in**: chuyển sang màn hình hỗ trợ điểm danh.

Dashboard giúp admin nắm nhanh tình trạng vận hành của toàn bộ portal mà không cần kiểm tra từng API riêng lẻ.

#### 3. Thêm hoặc chỉnh sửa sự kiện

Khi chọn **Thêm sự kiện mới**, hệ thống mở modal nhập thông tin sự kiện. Form này cho phép admin nhập tiêu đề, danh mục, tổng số ghế, thời gian, địa điểm, URL ảnh bìa và mô tả.

![Admin tạo sự kiện mới](/images/5-Workshop/event-portal-demo/06-admin-create-event-modal.png)

Luồng xử lý khi tạo sự kiện:

1. Admin nhập dữ liệu vào form.
2. Frontend kiểm tra các trường bắt buộc như tiêu đề, thời gian, địa điểm và tổng số ghế.
3. Frontend gửi request tạo sự kiện đến backend.
4. Backend tạo event metadata và ticket mặc định nếu cần.
5. Sau khi lưu thành công, danh sách sự kiện được refresh để hiển thị event mới.

Chức năng này chứng minh hệ thống không chỉ đọc dữ liệu mà còn hỗ trợ thao tác quản trị làm thay đổi dữ liệu backend.

#### 4. Xem danh sách thành viên của sự kiện

Từ dashboard, admin có thể chọn **Thành viên** để xem danh sách người đã đăng ký một sự kiện cụ thể.

![Admin xem danh sách thành viên](/images/5-Workshop/event-portal-demo/05-admin-members.png)

Màn hình thành viên hỗ trợ các tình huống:

- Kiểm tra user nào đã đăng ký sự kiện.
- Đối chiếu mã vé trước khi check-in.
- Theo dõi trạng thái người tham dự.
- Hỗ trợ ban tổ chức chuẩn bị danh sách check-in tại sự kiện.

Backend lấy dữ liệu registration theo event id, sau đó frontend hiển thị danh sách thành viên tương ứng với sự kiện được chọn.

#### 5. QR Check-in

Màn hình **QR Check-in** mô phỏng quá trình điểm danh tại cổng sự kiện. Admin chọn sự kiện, nhập hoặc quét ticket code và xác nhận check-in.

![Admin QR Check-in](/images/5-Workshop/event-portal-demo/07-admin-qr-checkin.png)

Các thành phần chính:

1. **Dropdown sự kiện**: chọn sự kiện cần điểm danh.
2. **Khu vực camera/QR**: mô phỏng thao tác bật camera để quét mã.
3. **Mã vé / QR payload**: cho phép nhập ticket code thủ công khi cần.
4. **Mã vé dùng để check-in**: các ticket code có sẵn dùng trong quá trình xác minh check-in.
5. **Danh sách đã check-in**: hiển thị các vé đã được xác nhận.

Khi admin chọn một vé để quét, frontend gọi API check-in. Backend kiểm tra ticket code, cập nhật trạng thái `checkedIn`, sau đó trả kết quả về frontend để cập nhật giao diện.

#### 6. Tóm tắt luồng Admin

Luồng Admin có thể tóm tắt như sau:

```text
Đăng nhập admin -> Mở dashboard -> Quản lý sự kiện -> Xem thành viên -> Check-in người tham dự
```

Luồng này chứng minh hệ thống đã có các chức năng vận hành cốt lõi cho ban tổ chức sự kiện: theo dõi dữ liệu, quản lý sự kiện, kiểm tra danh sách người tham gia và hỗ trợ điểm danh.
