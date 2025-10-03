# Các bước cài đặt Rocky Linux

## Bước 1: Tải file ISO 

Truy cập trang tải chính thức của Rocky Linux và chọn phiên bản ISO phù hợp (DVD, Boot, Minimal).

[Rocky](https://rockylinux.org/vi-VN/download)

Ở đây ta chọn bản Rocky Linux 9 bản Minimal iso cho nhẹ.

![rk1](/../2.VMWare/images/rk1.png)

## Bước 2: Tạo máy ảo trên VMware 

Làm tương tự hướng dẫn trong link trên: [Tạo máy ảo](https://github.com/Quyen-TT/system-intership/blob/main/QuyenNV/2.VMWare/docs/vmware.md)

## Bước 3: Quá trình cài đặt

**Chọn ngôn ngữ:**

![rk2](/../2.VMWare/images/rk2.png)

**Bảng tóm tắt các thiết lập (Installation Summary):**

Trên màn hình này bạn sẽ cấu hình các mục như:

- Bố cục bàn phím (Keyboard Layout)

- Hỗ trợ ngôn ngữ (Language Support)

- Thời gian & múi giờ (Time & Date)

- Lựa chọn phần mềm (Software Selection)

- Ổ đĩa & phân vùng (Installation Destination)

- Mật khẩu root và tạo người dùng (Root Password & User Creation)

![rk3](/../2.VMWare/images/rk3.png)

**Installation Destination:**

Trong mục `Installation Destination`, ta chọn `Custom`, nhấn `Done` để mở cửa sổ `Manual Partitioning`

![rk4](/../2.VMWare/images/rk4.png)

Trong cửa sổ Manual Partitioning, bạn sẽ tự tạo các phân vùng và chọn hệ thống tệp (filesystem) cho từng phân vùng.

- Trong menu xổ xuống, chọn Standard Partition làm kiểu phân vùng.

- Nhấn nút `+` để thêm phân vùng mới.

- Mỗi lần tạo phân vùng, nhập dung lượng và nhấn Add mount point để xác nhận.

- Sau khi hoàn tất, nhấn Done để thoát khỏi trình quản lý phân vùng.

![rk5](/../2.VMWare/images/rk5.png)

Ở đây, ta sẽ tạo các phân vùng như sau:

- `/`: 31 GiB

- `/boot`: 1 GiB

- `swap`: 8 GiB

![rk6](/../2.VMWare/images/rk6.png)

Hệ thống sẽ hiển thị cửa sổ Summary of Changes (tóm tắt các thay đổi phân vùng):

- Nhấn Accept Changes để ghi thay đổi lên ổ đĩa.

- Nhấn Cancel nếu muốn quay lại và chỉnh sửa lại các phân vùng.

![rk7](/../2.VMWare/images/rk7.png)

**Mật khẩu root:**  

![rk8](/../2.VMWare/images/rk8.png)

**Tạo người dùng mới:**

![rk9](/../2.VMWare/images/rk9.png)

Ta có thể chọn `Make this user administrator` để cấp quyền sudo

**Bắt đầu cài đặt:**

Khi mọi thiết lập đã xong, nhấn `Begin Installation`

![rk10](/../2.VMWare/images/rk10.png)

Quá trình cài đặt diễn ra

![rk11](/../2.VMWare/images/rk11.png)

Nhấn `Reboot System` để khởi động vào hệ thống Rocky Linux mới

**Quá trình cài đặt hoàn tất:**

![rk12](/../2.VMWare/images/rk12.png)