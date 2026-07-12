---
title : "Demo luồng User và Admin"
date : 2026-07-12
weight : 7
chapter : false
pre : " <b> 5.7. </b> "
---

#### Mục tiêu của phần demo

Sau khi hoàn thành các bước triển khai backend và frontend trong workshop, phần này ghi lại quá trình chạy thử **AWS Serverless Event Portal** trên các dịch vụ AWS đã triển khai. Mục tiêu không chỉ là chụp màn hình kết quả, mà còn giải thích cách từng chức năng hoạt động trong hai vai trò chính của hệ thống:

- **User**: người tham dự sự kiện, có thể xem danh sách sự kiện, đăng ký tài khoản, đăng nhập, xem chi tiết sự kiện, đăng ký vé và quản lý vé cá nhân.
- **Admin**: người quản trị hệ thống, sử dụng tài khoản được cấp sẵn để xem dashboard tổng quan, quản lý sự kiện, xem danh sách thành viên và hỗ trợ check-in bằng QR/ticket code.

Trong quá trình demo, frontend React/Vite được host dưới dạng static website trên Amazon S3, còn backend API được cung cấp thông qua Amazon API Gateway và xử lý bằng AWS Lambda. Dữ liệu của ứng dụng được lấy từ các backend services đã deploy, vì vậy phần demo phản ánh đúng hơn kiến trúc serverless của project.

#### 1. Bắt đầu từ màn hình đăng nhập

Khi người dùng chọn **Đăng nhập**, ứng dụng mở form xác thực. Form này dùng chung cho cả User và Admin. User thông thường có thể đăng ký và đăng nhập trực tiếp trên ứng dụng, còn Admin sử dụng tài khoản đã được chuẩn bị và cấp sẵn.

![Màn hình đăng nhập EventPortal](/images/5-Workshop/event-portal-demo/00-login-page.png)

Màn hình đăng nhập gồm các thành phần chính:

1. Trường **Email** dùng để xác định tài khoản.
2. Trường **Mật khẩu** dùng để mô phỏng xác thực.
3. Tài khoản admin được cấp sẵn dùng để truy cập vai trò quản trị.
4. Liên kết **Đăng ký ngay** dành cho user mới.

Khi đăng nhập thành công, các request cần xác thực sẽ được gửi đến backend API đã triển khai. Backend dựa vào vai trò của tài khoản để xác định người dùng hiện tại là User hay Admin.

#### 2. Đăng ký tài khoản người dùng mới

Nếu chưa có tài khoản, người tham dự có thể chuyển sang form đăng ký. Form đăng ký yêu cầu nhập họ tên, email và mật khẩu để tạo tài khoản user phục vụ việc đăng ký sự kiện.

![Màn hình đăng ký tài khoản](/images/5-Workshop/event-portal-demo/00-register-page.png)

Luồng đăng ký giúp kiểm thử các bước:

1. User nhập thông tin cơ bản.
2. Frontend gọi hàm đăng ký trong AuthContext.
3. Backend authentication flow xử lý yêu cầu đăng ký.
4. Sau khi tài khoản được tạo, user có thể đăng nhập và sử dụng các chức năng đăng ký sự kiện.

Tài khoản Admin không được tạo thông qua form đăng ký công khai này. Admin sẽ được chuẩn bị và cấp tài khoản riêng để đảm bảo chỉ người có quyền mới truy cập được các chức năng quản trị.

#### 3. Trang chủ sau khi kết nối backend

Sau khi mở ứng dụng, trang chủ hiển thị danh sách sự kiện lấy từ backend API. Các chỉ số như tổng sự kiện, tổng lượt đăng ký và tỉ lệ lấp đầy được tính dựa trên dữ liệu backend trả về.

![Trang danh sách sự kiện](/images/5-Workshop/event-portal-demo/01-homepage-events.png)

Các chức năng chính trên trang chủ:

- Hiển thị danh sách sự kiện dưới dạng event card.
- Tìm kiếm sự kiện theo tên hoặc nội dung.
- Lọc sự kiện theo danh mục như Công nghệ, Âm nhạc hoặc Giáo dục.
- Mở trang chi tiết để xem thông tin đầy đủ và thao tác đăng ký.

#### 4. Chia luồng demo theo vai trò

Để dễ theo dõi, phần demo chi tiết được tách thành hai mục nhỏ:

1. [Luồng người dùng User](5.7.1-User-flow/)
2. [Luồng quản trị Admin](5.7.2-Admin-flow/)

Cách tách này giúp giải thích rõ hơn trách nhiệm của từng vai trò. User tập trung vào trải nghiệm tham gia sự kiện, còn Admin tập trung vào quản lý sự kiện và vận hành check-in.

#### 5. Kết luận nhanh

Qua phần demo tổng quan, hệ thống đã thể hiện được một luồng hoạt động đầy đủ từ đăng ký/đăng nhập đến sử dụng chức năng theo vai trò. Frontend không chỉ hiển thị giao diện tĩnh mà đã gọi các AWS backend APIs để lấy danh sách sự kiện, vé, đăng ký và dữ liệu quản trị.
