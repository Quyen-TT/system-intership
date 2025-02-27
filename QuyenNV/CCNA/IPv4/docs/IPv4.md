# Tìm hiểu về IPv4

## 1. IPv4 là gì?

IPv4 (Internet Protocol version 4) là phiên bản thứ tư của giao thức Internet (IP), được sử dụng để định danh và định tuyến các thiết bị trong mạng máy tính. IPv4 sử dụng địa chỉ 32 bit, được biểu diễn dưới dạng bốn nhóm số thập phân, mỗi nhóm từ 0 đến 255, cách nhau bằng dấu chấm (ví dụ: 192.168.1.1).

## 2. Tại sao lại không có IPv1,v2,v3,v5?

**IPv1, IPv2, IPv3:**

Ba phiên bản này được phát triển vào những năm 1970 và đầu 1980 trong quá trình nghiên cứu và thử nghiệm giao thức mạng:

* **IPv1 (1974):** Là một phần của NCP (Network Control Protocol), một giao thức mạng tiền thân của TCP/IP.

* **IPv2 (1978):** Một bản cải tiến, nhưng vẫn còn nhiều hạn chế về hiệu suất và khả năng mở rộng.

* **IPv3 (1979-1981):** Thử nghiệm thêm các tính năng như loại dịch vụ (Type of Service) nhưng vẫn chưa đủ mạnh.

Cả ba phiên bản này đều mang tính thử nghiệm và không đủ linh hoạt để triển khai rộng rãi, nên chúng nhanh chóng được thay thế bởi IPv4 (1981), phiên bản đầu tiên được áp dụng thực tế.

**IPv5:**

IPv5 thực sự đã tồn tại dưới dạng một giao thức thử nghiệm có tên **Internet Stream Protocol (ST, rồi đến ST-II)**, được thiết kế để hỗ trợ truyền tải dữ liệu theo luồng (streaming). Tuy nhiên, IPv5 có các vấn đề như:

* Chỉ sử dụng địa chỉ 32-bit giống IPv4, không giải quyết được vấn đề thiếu địa chỉ.

* Không được thiết kế để sử dụng rộng rãi trên Internet mà chỉ dành cho một số ứng dụng cụ thể.

Vì vậy, IPv5 không bao giờ trở thành tiêu chuẩn chính thức và bị bỏ qua để nhường chỗ cho IPv6, một giao thức với không gian địa chỉ 128-bit khắc phục hoàn toàn vấn đề của IPv4.

## 3. Cấu trúc của IPv4?

Địa chỉ IPv4 gồm 32 bit nhị phân, chia thành 4 cụm 8 bit (gọi là các octet). Các octet được biểu diễn dưới dạng thập phân và được ngăn cách nhau bằng các dấu chấm.

![Hình 1](/QuyenNV/CCNA/IPv4/images/anh1.png)

Các quy tắc đặt địa chỉ IP:

* Các bit phần mạng không được phép đồng thời bằng 0.  
VD: địa chỉ 0.0.0.1 với phần mạng là 0.0.0 và phần host là 1 là không hợp lệ.  

* Nếu các bit phần host đồng thời bằng 0, ta có một địa chỉ mạng.  
VD: địa chỉ 192.168.1.1 là một địa chỉ có thể gán cho host nhưng địa chỉ 192.168.1.0 là một địa chỉ mạng, không thể gán cho host được.

* Nếu các bit phần host đồng thời bằng 1, ta có một địa chỉ quảng bá (broadcast).  
VD: địa chỉ 192.168.1.255 là một địa chỉ broadcast cho mạng 192.168.1.0

## 4. Các thành phần của IPv4

Địa chỉ IP được chia thành hai phần: phần mạng (network) và phần máy chủ (host).

* Phần mạng (Network ID): Xác định mạng mà thiết bị thuộc về.

* Phần máy chủ (Host ID): Xác định thiết bị cụ thể trong mạng đó.

## 5. Các lớp của IPv4

Địa chỉ IP được chia thành 5 lớp A, B, C, D và E.

![Hình 2](/QuyenNV/CCNA/IPv4/images/anh2.png)

- Lớp A:  
  - Địa chỉ lớp A sử dụng một octet đầu làm phần mạng, ba octet sau làm phần host.
  - Bit đầu của một địa chỉ lớp A luôn được giữ là 0.
  - Các địa chỉ mạng lớp A gồm: 1.0.0.0 à 127.0.0.0.
  - Địa chỉ 127.0.0.1 là địa chỉ loopback trên các host nên địa chỉ mạng lớp A sử dụng được gồm 1.0.0.0 à 126.0.0.0 (126 mạng).
  - Phần host có 24 bit => mỗi mạng lớp A có (2^24 – 2) host.

![Hình 3](/QuyenNV/CCNA/IPv4/images/anh3.png)

- Lớp B: 
  - Địa chỉ lớp B sử dụng 2 octet đầu làm phần mạng, 2 octet sau làm phần host. 
  - 2 bit đầu của một IP lớp B sẽ luôn là 1 0.
  - Các địa chỉ mạng lớp B sẽ bao gồm: 128.0.0.0 -> 191.255.0.0.
  - Có tất cả 2^14 mạng trong lớp B.
  - Phần host: 16 bit => Một mạng lớp B có 2^16 – 2 host.

![Hình 4](/QuyenNV/CCNA/IPv4/images/anh4.png)

- Lớp C:
  - Địa chỉ lớp C sử dụng ba octet đầu làm phần mạng, một octet sau làm phần host.
  - Ba bit đầu của một địa chỉ lớp C luôn được giữ là 110.
  - Các địa chỉ mạng lớp C gồm: 192.0.0.0 -> 223.255.255.0.
  - Có tất cả 2^21 mạng trong lớp C.
  -   Phần host: 8 bit => Một mạng lớp C có 2^8 – 2 = 254 host.

![Hình 5](/QuyenNV/CCNA/IPv4/images/anh5.png)

- Lớp D:
  - Bao gồm các địa chỉ trong dải: 224.0.0.0 -> 239.255.255.255
  - Dùng làm địa chỉ multicast.

- Lớp E:
  - Từ 240.0.0.0 trở đi.
  - Được dùng cho mục đích dự phòng.

**_Chú ý:_**

* Các lớp địa chỉ IP có thể sử dụng để đặt cho các host là các lớp A, B, C.

* Để thuận tiện cho việc nhận diện một địa chỉ IP thuộc lớp nào, ta quan sát octet đầu của địa chỉ, nếu octet này có giá trị:  

| Dải địa chỉ IP   | Lớp địa chỉ |
|:----------------:|:----------: |
| 1 - 126          | Lớp A       |
| 128 - 191        | Lớp B       |
| 192 - 223        | Lớp C       |
| 224 - 239        | Lớp D       |
| 240 - 255        | Lớp E       |


## 6. So sánh IP Public và IP Private

- **IP Public:**
  - Là địa chỉ IP sử dụng cho các gói tin đi trên môi trường Internet, được định tuyến trên môi trường Internet, không sử dụng trong mạng LAN.
  - Địa chỉ public phải là duy nhất cho mỗi host tham gia vào Internet.

- **IP Private:**
  - Chỉ được sử dụng trong mạng nội bộ (mạng LAN), không được định tuyến trên môi trường Internet.
  - Có thể được sử dụng lặp đi lặp lại trong các mạng LAN khác nhau.
  - IP Private được sử dụng để bảo tồn địa chỉ IP public đang dần cạn kiệt.  
  - Dải địa chỉ private (được quy định trong RFC 1918):

    | Lớp | Dải địa chỉ Private |
    |:-----|:--------------------|
    | Lớp A | `10.x.x.x` |
    | Lớp B | `172.16.x.x -> 172.31.x.x` |
    | Lớp C | `192.168.x.x` |

- **Kỹ thuật NAT (Network Address Translation)** được sử dụng để chuyển đổi giữa IP private và IP public.

- **Sự khác biệt giữa địa chỉ IP Private và địa chỉ IP Public**

| **Đặc điểm** | **Địa chỉ IP Private** | **Địa chỉ IP Public** |
|-------------|----------------------|----------------------|
| **Phạm vi** | Cục bộ | Toàn cầu |
| **Mục đích sử dụng** | Giao tiếp trong mạng nội bộ | Giao tiếp bên ngoài mạng |
| **Đặc điểm địa chỉ** | IP private của các hệ thống trong mạng sẽ khác nhau nhưng vẫn theo một quy luật thống nhất | IP public có thể khác nhau theo quy luật đồng nhất hoặc không đồng nhất |
| **Hoạt động trong** | Chỉ hoạt động trong mạng LAN | Sử dụng để truy cập dịch vụ Internet |
| **Quản lý bởi** | Được sử dụng để load hệ điều hành mạng | Được kiểm soát bởi ISP (nhà cung cấp dịch vụ Internet) |
| **Chi phí** | Có sẵn miễn phí | Không miễn phí |
| **Cách tìm địa chỉ IP** | Nhập `ipconfig` vào Command Prompt | Gõ “what is my IP” vào Google |
| **Phạm vi địa chỉ** | `10.0.0.0 – 10.255.255.255`<br>`172.16.0.0 – 172.31.255.255`<br>`192.168.0.0 – 192.168.255.255` | Ngoại trừ các địa chỉ IP private, toàn bộ phần còn lại đều là địa chỉ IP public |

## 7. Phân biệt địa chỉ Broadcast và địa chỉ Multicast

### 7.1 Địa chỉ Broadcast

Địa chỉ Broadcast là một loại địa chỉ IP được sử dụng để gửi dữ liệu đến tất cả các thiết bị trong cùng một mạng. Khi một gói tin được gửi đến địa chỉ Broadcast, mọi thiết bị trong mạng đều nhận được và xử lý gói tin đó.

Địa chỉ Broadcast có hai loại chính: 

- Directed Broadcast: Gửi đến tất cả thiết bị trong một mạng cụ thể. Ví dụ: 192.168.1.255.

- Local Broadcast: Gửi đến tất cả thiết bị trong mạng hiện tại. Ví dụ: 255.255.255.255.

![Hình 7](/QuyenNV/CCNA/IPv4/images/anh7.png)

### 7.2 Địa chỉ Multicast

Địa chỉ Multicast là một loại địa chỉ IP được sử dụng để gửi dữ liệu đến một nhóm thiết bị nhất định thay vì tất cả thiết bị trong mạng. Chỉ những thiết bị thuộc nhóm Multicast mới nhận được gói tin, giúp tiết kiệm băng thông mạng.

Địa chỉ Multicast sử dụng dải địa chỉ IP từ 224.0.0.0 đến 239.255.255.255

![Hình 6](/QuyenNV/CCNA/IPv4/images/anh6.png)


## 8. Subnet, subnet mask, prefex

Subnet (subnetwork - mạng con) là một phần của một mạng lớn hơn, giúp chia nhỏ một mạng IP thành các phần nhỏ hơn để cải thiện hiệu suất, bảo mật và quản lý mạng dễ dàng hơn.

Subnet mask là một dải 32 bit nhị phân đi kèm với một địa chỉ IP, được các host sử dụng để xác định địa chỉ mạng của địa chỉ IP này. Để làm được điều đó, host sẽ đem địa chỉ IP thực hiện phép tính AND từng bit một của địa chỉ với subnet mask của nó, kết quả host sẽ thu được địa chỉ mạng tương ứng của địa chỉ IP.

![Hình 9](/QuyenNV/CCNA/IPv4/images/anh9.png)

Số prefix: Subnet mask được sử dụng kèm với địa chỉ IP để một host có thể căn cứ vào đó xác dịnh được địa chỉ mạng tương ứng của địa chỉ này. Vì
vậy, khi khai báo một địa chỉ IP luôn phải khai báo kèm theo một subnet mask. Tuy nhiên, subnet mask dù đã được viết dưới dạng số thập phân vẫn khá dài dòng nên để mô tả một địa chỉ IP một cách ngắn gọn hơn, người ta dùng một đại lượng được gọi là số prefix. Số prefix có thể hiểu một cách đơn giản là số bit mạng trong một địa chỉ IP, được viết ngay sau địa chỉ IP, và được ngăn cách với địa chỉ này bằng một dấu “/”.

# Tài liệu tham khảo

[Chương 1 - Địa chỉ IPv4, Chia subnet, VLSM, Summary - VnPro](https://vnpro.vn/thu-vien/chuong-1-dia-chi-ipv4-chia-subnet-vlsm-summary-4108.html)

