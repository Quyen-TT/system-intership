# Cài đặt VMware

## 1. Cài đặt VMware

Truy cập trang web chính thức của hãng để tải.

[VMWare](https://vmware.com/in.html)

## 2. Tạo máy ảo trên VMware

### 2.1 Chuẩn bị

Cài đặt thành công VMWare

Cài đặt file iso CentOS Stream 9, Ubuntu 24.04, Windows 2025 Server 

### 2.2 Tạo máy ảo

Bước 1: Tại cửa sổ chính của VMware, chọn Create a New Virtual Machine để tiến hành tạo máy ảo mới.

![vm1](/QuyenNV/VMWare/images/vm.png)

Bước 2: Chọn Installer disc image file (iso) và bấm vào Browse để chọn file iso.

![vm2](/QuyenNV/VMWare/images/vm2.png)

Bước 3: khai báo ổ cứng ảo, điền tên, chọn thư mục lưu.

![vm3](/QuyenNV/VMWare/images/vm3.png)

Bước 4: Thiết lập dung lượng, cách lưu cho ổ cứng ảo.

![vm4](/QuyenNV/VMWare/images/vm4.png)

Bước 5: Bấm Finish, VMware sẽ tự động khởi chạy máy ảo.

## 3. Các chế độ network trong VMware

### 3.1 Chế độ Bridge

Virtual Ethernet adapter trên VM sẽ kết nối đến VMnet0 switch và thông qua Virtual bridge để kết nối đến Host Ethernet adapter. Vậy nên trong trường hợp này sẽ không có VMnet Card nào được tạo thêm. Lúc này VM và Host sẽ cùng chung đường mạng và VM có thể nhận IP tự động từ DHCP server hoặc thiết lập thủ công. Như vậy trên đường mạng này, tương tác của máy ảo và các thành phần khác sẽ có tính 2 chiều giống như Host.

![anh1](/QuyenNV/VMWare/images/anh1.png)

### 3.2 Chế độ NAT

Virtual Ethernet adapter trên VM sẽ kết nối đến VMnet8 switch và nhờ hỗ trợ của NAT device để kết nối đến mạng vật lý bên ngoài (nhưng các thiết bị ngoài mạng vật lý không thể chủ động khởi tạo kết nối đến máy ảo). Lúc này VM và Host sẽ cùng khác đường mạng và VM có thể nhận IP tự động từ DHCP server hoặc thiết lập thủ công. Trong trường hợp này, khi kiểm tra Network Connections trên Host, sẽ thấy có thêm VMware Network Adapter VMnet8 được tạo ra.

![anh2](/QuyenNV/VMWare/images/anh2.png)

### 3.3 Chế độ Host-only

Virtual Ethernet adapter trên VM và Host Ethernet adapter sẽ cùng kết nối đến VMnet1 switch để tạo thành một mạng cô lập (chỉ có VM và Host giao lưu phối hợp với nhau và VM không có kết nối đến mạng vật lý bên ngoài). Lúc này VM và Host sẽ cùng chung đường mạng và VM có thể nhận IP tự động từ DHCP server hoặc thiết lập thủ công. Trong trường hợp này, khi kiểm tra Network Connections trên Host, sẽ thấy có thêm VMware Network Adapter VMnet1 được tạo ra.
 
![anh3](/QuyenNV/VMWare/images/anh3.png)

## 4. Sử dụng chế độ mạng NAT cho các máy ảo để truy cập internet

**Địa chỉ IP máy Ubuntu:**

![anh4](/QuyenNV/VMWare/images/anh11.png)

**Ping từ máy ảo đến google.com:**

![anh5](/QuyenNV/VMWare/images/anh12.png)

## 5. Sử dụng chế độ card Host-only để 2 máy ảo kết nối với nhau

**Địa chỉ IP máy Centos:**

![anh6](/QuyenNV/VMWare/images/anh13.png)

**Địa chỉ IP máy Ubuntu:**

![anh7](/QuyenNV/VMWare/images/anh6.png)

**Ping giữa 2 máy:**

![anh8](/QuyenNV/VMWare/images/anh7.png)

## 6. Sử dụng 1 card Bridge để từ máy ảo ping ra máy laptop cá nhân

**Địa chỉ IP máy laptop:**

![anh9](/QuyenNV/VMWare/images/anh8.png)

**Địa chỉ IP máy Ubuntu:**

![anh10](/QuyenNV/VMWare/images/anh9.png)

**Ping giữa 2 máy:**

![anh11](/QuyenNV/VMWare/images/anh10.png)

## 7. SNAT và DNAT

### 7.1 SNAT

SNat tĩnh hay còn gọi là Static NAT là phương thức NAT một đổi một. Nghĩa là một địa chỉ IP cố định trong LAN sẽ được ánh xạ ra một địa chỉ IP Public cố định trước khi gói tin đi ra Internet. Phương pháp này không nhằm tiết kiệm địa chỉ IP mà chỉ có mục đích ánh xạ một IP trong LAN ra một IP Public để ẩn IP nguồn trước khi đi ra Internet làm giảm nguy cơ bị tấn công trên mạng.

Phương án này có nhược điểm là nếu trong LAN có bao nhiêu IP muốn đi ra Internet thì ta phải có từng đó IP Public để ánh xạ. Do vậy phương án NAT tĩnh chỉ được đúng với các máy chủ với nhiệm vụ Public các Server này lên Internet.

![anh12](/QuyenNV/VMWare/images/anh4.png)

### 7.2 DNAT

Nat động (Dynamic NAT) là một giải pháp tiết kiệm IP Public cho NAT tĩnh. Thay vì ánh xạ từng IP cố định trong LAN ra từng IP Public cố định. LAN động cho phép NAT cả dải IP trong LAN ra một dải IP Public cố định ra bên ngoài.

Ví dụ: Hệ thống LAN trong công ty có 100 IP, nếu muốn 100 IP này truy cập Internet thì theo phương án NAT tĩnh công ty sẽ phải thuê từ ISP 100 IP 
Public. Điều này quá tốn kém, giải pháp NAT động cho phép chỉ cần thuê từ ISP 10 IP Public nếu tại cùng một thời điểm chỉ có 10 IP trong LAN truy cập Internet. Tuy nhiên giải pháp NAT động vẫn có hạn chế vì nếu tại một thời điểm công ty cần 20 IP trong LAN truy cập Internet thì mười IP truy cập sau sẽ phải đợi đến khi nào có IP rỗi (các IP trước không chiếm dụng IP Public nữa) thì mới có thể truy cập Internet được. Chính vì thế giải pháp NAT động ít khi được sử dụng.

![anh13](/QuyenNV/VMWare/images/anh5.png)

## 8. Cài đặt địa chỉ IP tĩnh cho Linux

### Trên Ubuntu:

**Địa chỉ IP ban đầu trên Ubuntu:**

![anh14](/QuyenNV/VMWare/images/anh11.png)

**Để cài đặt IP tĩnh, chỉnh sửa file .yaml trong thư mục /etc/netplan**

![anh15](/QuyenNV/VMWare/images/anh14.png)

    sudo nano /etc/netplan/01-netcfg.yaml

![anh16](/QuyenNV/VMWare/images/anh15.png)

**Chạy lệnh netplan apply để áp dụng:** 

    sudo netplan apply

**Địa chỉ IP Ubuntu sau khi cấu hình IP tĩnh:**

![anh17](/QuyenNV/VMWare/images/anh16.png)

### Trên Centos:

**Địa chỉ IP ban đầu trên Centos:**

![anh18](/QuyenNV/VMWare/images/anh18.png)

**Để cài đặt IP tĩnh, sử dụng các câu lệnh:**

    nmcli con mod ens160 ipv4.addresses 192.168.91.101/24
    nmcli con mod ens160 ipv4.gateway 192.168.91.1
    nmcli con mod ens160 ipv4.dns 8.8.8.8
    nmcli con mod ens160 ipv4.method manual

**Sử dụng câu lệnh dưới đây để áp dụng:** 

    nmcli con up ens160

**Địa chỉ IP Centos sau khi cấu hình IP tĩnh:**

![anh19](/QuyenNV/VMWare/images/anh18.png)



