---
title : "Luồng người dùng User"
date : 2026-07-12
weight : 1
chapter : false
pre : " <b> 5.7.1. </b> "
---

#### Mục tiêu của luồng User

Luồng User thể hiện trải nghiệm của một người tham dự sự kiện trên website Event Portal. Người dùng bắt đầu từ đăng ký hoặc đăng nhập, sau đó xem danh sách sự kiện, mở chi tiết, đăng ký vé và theo dõi trạng thái tham dự sau khi được admin check-in/check-out.

#### 1. Đăng ký hoặc đăng nhập

Người tham dự mới có thể chọn **Đăng ký ngay** để tạo tài khoản user. Form đăng ký yêu cầu họ tên, email và mật khẩu. Sau khi tạo tài khoản, user có thể đăng nhập và sử dụng các chức năng đăng ký sự kiện.

![Màn hình đăng ký tài khoản](/images/5-Workshop/event-portal-demo/00-register-page.png)

Nếu đã có tài khoản, user dùng màn hình đăng nhập để vào hệ thống.

![Màn hình đăng nhập EventPortal](/images/5-Workshop/event-portal-demo/00-login-page.png)

Sau khi đăng nhập, thanh điều hướng hiển thị thêm mục **Vé của tôi** và **Hồ sơ**. Đây là dấu hiệu cho thấy user đã có phiên đăng nhập và có thể truy cập các chức năng cá nhân.

#### 2. Xem danh sách sự kiện

Trang chủ hiển thị toàn bộ sự kiện mà backend trả về. Mỗi event card gồm ảnh bìa, danh mục, thời gian, tên sự kiện, địa điểm, mô tả ngắn và số ghế còn trống.

![Trang danh sách sự kiện](/images/5-Workshop/event-portal-demo/01-homepage-events.png)

Các thao tác chính:

1. **Tìm kiếm** sự kiện theo tên hoặc mô tả.
2. **Lọc danh mục** để xem nhóm sự kiện tương ứng.
3. **Xem chi tiết** bằng cách nhấn vào event card.
4. **Theo dõi sức chứa** trước khi đăng ký.

Frontend gọi API danh sách sự kiện từ backend. Nếu có filter danh mục hoặc từ khóa, frontend gửi thêm query để backend trả về dữ liệu phù hợp.

#### 3. Xem chi tiết và đăng ký vé

Khi user chọn một sự kiện, trang chi tiết hiển thị đầy đủ thông tin như thời gian, địa điểm, mô tả và tình trạng chỗ ngồi.

![User xem chi tiết sự kiện và vé](/images/5-Workshop/event-portal-demo/02-user-event-detail-ticket.png)

Nếu user chưa đăng ký, khu vực bên phải hiển thị nút **Đăng ký vé**. Khi nhấn đăng ký, frontend gọi API đăng ký sự kiện. Backend tạo registration record, sinh ticket code và trả thông tin vé về frontend.

Sau khi đăng ký thành công, user nhìn thấy ticket card với mã vé. Mã này có thể được dùng tại cổng sự kiện để admin quét QR hoặc nhập thủ công khi check-in/check-out.

#### 4. Kiểm tra vé đã đăng ký

User có thể mở mục **Vé của tôi** để xem lại các vé đang sở hữu.

![User xem danh sách vé đã đăng ký](/images/5-Workshop/event-portal-demo/03-user-my-tickets.png)

Màn hình này giúp user:

1. Xác nhận đã đăng ký sự kiện thành công.
2. Xem mã vé/ticket code của từng sự kiện.
3. Quay lại trang chi tiết sự kiện khi cần.
4. Đối chiếu vé khi tham dự sự kiện.

#### 5. Xem lịch sử tham dự

Sau khi hệ thống có thêm check-out, user có thể theo dõi vòng đời tham dự của từng vé trong tab **Lịch sử tham dự** ở trang **Hồ sơ**. Đây là phần giúp user biết vé của mình đang ở trạng thái nào sau khi admin xử lý tại cổng sự kiện.

![User xem lịch sử tham dự sự kiện](/images/5-Workshop/event-portal-demo/08-user-attendance-history.png)

Các trạng thái cần giải thích trong ảnh:

1. **Đã đăng ký**: user đã có vé nhưng chưa đến cổng check-in.
2. **Đã check-in**: admin đã xác nhận user có mặt tại sự kiện.
3. **Đã check-out**: admin đã xác nhận user rời sự kiện hoặc hoàn tất lượt tham dự.

Mỗi item trong lịch sử tham dự hiển thị tên sự kiện, thời gian, địa điểm, mã vé, thời điểm đăng ký, thời điểm check-in và thời điểm check-out nếu có. Dữ liệu này được lấy từ API registration của user, sau đó frontend kết hợp với thông tin event để hiển thị đầy đủ.

#### 6. Tóm tắt luồng User

Luồng User có thể tóm tắt như sau:

```text
Mở ứng dụng -> Đăng ký/Đăng nhập -> Xem danh sách sự kiện -> Xem chi tiết -> Đăng ký vé -> Xem Vé của tôi -> Xem Lịch sử tham dự
```

Luồng này chứng minh ứng dụng đã hỗ trợ các chức năng cốt lõi cho người tham dự: tìm sự kiện, đăng ký vé, sử dụng mã vé tại cổng và theo dõi lại trạng thái tham dự sau sự kiện.

