# Tìm hiểu về FTP 

## 1. FTP là gì?

FTP (File Transfer Protocol) là một giao thức được sử dụng để truyền tải dữ liệu giữa máy tính và máy chủ trên mạng internet. Giao thức này cho phép người dùng truy cập và chia sẻ tệp tin trên các máy chủ từ xa thông qua việc truyền tải dữ liệu qua mạng. FTP thường được sử dụng để tải lên hoặc tải xuống các tệp tin, quản lý website và sao lưu dữ liệu từ xa.

![anh1](/QuyenNV/FTP/images/anh1.png)

## 2. FTP dùng để làm gì?

### 2.1. Upload và Download file lên Web Hosting

Đây có lẽ là ứng dụng quen thuộc nhất của FTP đối với những người làm website. Các nhà cung cấp web hosting thường cấp tài khoản FTP cho người dùng để họ có thể dễ dàng tải lên (upload) các tệp mã nguồn, hình ảnh, video, theme, plugin… lên máy chủ hosting hoặc tải về (download) các tệp từ hosting về máy tính cá nhân để chỉnh sửa hoặc lưu trữ. Việc này rất cần thiết khi xây dựng, cập nhật và quản lý website.

### 2.2. Sao lưu (Backup) và Phục hồi (Restore) dữ liệu Website

FTP là một công cụ hữu ích để thực hiện việc sao lưu website thủ công. Người dùng có thể sử dụng FTP client để kết nối vào hosting và tải toàn bộ thư mục chứa mã nguồn, dữ liệu website về máy tính của mình. Ngược lại, khi cần phục hồi dữ liệu (ví dụ sau sự cố), người dùng cũng có thể dùng FTP để tải bản sao lưu từ máy tính lên lại hosting.

### 2.3. Chia sẻ tệp tin dung lượng lớn

Khi cần chia sẻ file lớn (ví dụ: video chất lượng cao, bộ cài phần mềm, tài liệu dự án lớn) mà các phương thức như email (thường giới hạn dung lượng đính kèm) hay các dịch vụ lưu trữ đám mây miễn phí (có thể giới hạn tốc độ hoặc dung lượng) không đáp ứng được, FTP trở thành một giải pháp hiệu quả. Người dùng có thể thiết lập một FTP server tạm thời hoặc sử dụng dịch vụ FTP để cho phép người khác tải về các tệp tin này.

## 3. Nguyên lí hoạt động 

![anh2](/QuyenNV/FTP/images/anh2.png)

### 3.1. Các kênh kết nối: Control và Data Connection

Kênh Điều Khiển (Control Connection): Kênh này thường được thiết lập trên cổng (port) 21 của máy chủ. Nó dùng để truyền các lệnh từ client (ví dụ: USER, PASS để đăng nhập; LIST để xem danh sách file; RETR để tải file) và nhận các phản hồi trạng thái từ server. Kênh này được duy trì trong suốt phiên làm việc FTP.

Kênh Dữ Liệu (Data Connection): Kênh này được tạo ra khi có yêu cầu truyền dữ liệu thực tế (nội dung file hoặc danh sách thư mục). Nó thường sử dụng cổng 20 trên máy chủ (trong Active mode) hoặc một cổng ngẫu nhiên (trong Passive mode). Kênh này chỉ tồn tại trong thời gian truyền dữ liệu và sẽ đóng lại sau khi hoàn tất.

### 3.2. Các chế độ kết nối: Active Mode và Passive Mode

**Active Mode (Chế độ Chủ động)**

- Client kết nối từ một cổng ngẫu nhiên (N) đến cổng 21 của Server (Control Connection).

- Client thông báo cho Server biết nó sẽ lắng nghe trên cổng N+1 (bằng lệnh PORT).

- Server chủ động kết nối từ cổng 20 của nó đến cổng N+1 của Client để thiết lập Data Connection.

**Passive Mode (Chế độ Bị động)**

- Client kết nối từ một cổng ngẫu nhiên (N) đến cổng 21 của Server (Control Connection).

- Client gửi lệnh PASV đến Server.

- Server mở một cổng ngẫu nhiên (P) và thông báo cổng P này cho Client.

- Client chủ động kết nối từ cổng N+1 của nó đến cổng P của Server để thiết lập Data Connection.

### 4. Cấu trúc thành phần

Mô hình hoạt động của giao thức FTP gồm hai thành phần chính: máy khách (client) và máy chủ (server).

![anh3](/QuyenNV/FTP/images/anh3.png)

**Máy khách (Client)**

- Người dùng sử dụng một chương trình FTP client để kết nối với máy chủ FTP.

- Người dùng cung cấp thông tin đăng nhập như tên đăng nhập và mật khẩu để xác thực việc kết nối.

- Người dùng sử dụng client để tải lên hoặc tải xuống các tệp tin từ máy chủ FTP.

**Máy chủ (Server)**

- Máy chủ FTP chờ đợi các yêu cầu kết nối từ các máy khách.

- Khi một máy khách kết nối, máy chủ xác thực thông tin đăng nhập và quyết định xem máy khách có quyền truy cập vào các tệp tin và thư mục yêu cầu hay không.

- Máy chủ cung cấp dữ liệu được yêu cầu bởi máy khách và quản lý các hoạt động trên tệp tin và thư mục.

Mô hình hoạt động này cho phép người dùng truy cập và quản lý các tệp tin trên máy chủ từ xa thông qua việc truyền tải dữ liệu qua mạng.



