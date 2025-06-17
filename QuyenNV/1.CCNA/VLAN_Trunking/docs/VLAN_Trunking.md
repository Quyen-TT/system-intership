# Tìm hiểu về VLAN, trunking

## 1. VLAN

### 1.1. VLAN là gì? 

VLAN (Virtual Local Area Network) hay còn gọi là mạng LAN ảo là một kỹ thuật phân chia mạng LAN vật lý thành các mạng logic riêng biệt, được gọi là các VLAN.
  
Mỗi VLAN hoạt động như một mạng LAN riêng biệt, với lưu lượng truy cập riêng biệt và được cách ly với các VLAN khác.

![vlan1](/QuyenNV/1.CCNA/VLAN_Trunking/images/vlan1.png)

### 1.2. Phân loại VLAN

**Static VLAN (VLAN tĩnh)**

Static VLAN là loại VLAN được tạo ra bằng cách gắn các cổng Switch vào một VLAN. Cách làm này tương tự như việc một thiết bị được kết nối vào mạng và nó tự mình công nhận bản thân là VLAN của cổng đó.

Trong trường hợp người dùng cần thay đổi các cổng và có nhu cầu truy cập vào một VLAN chung, quản trị viên phải khai báo cổng cho VLAN trong lần kết nối tiếp theo.

**Dynamic VLAN (VLAN động)**

Được biết Dynamic VLAN là loại VLAN được tạo ra bằng cách sử dụng những phần mềm điển hình như Ciscowork 2000. Khi này người dùng sẽ sử dụng VLAN Management Policy Server (VMPS) để đăng ký các cổng Switch kết nối tới VLAN tự động. Quá trình kết nối được thực hiện dựa trên địa chỉ MAC nguồn của loại thiết bị được kết nối tới cổng.

Tương tự như mô hình thiết bị mạng, Dynamic VLAN hoạt động truy vấn một cơ sở dữ liệu dựa trên VMPS của các VLAN thành viên còn lại.

### 1.3. Cách hoạt động VLAN 

![vlan5](/QuyenNV/1.CCNA/VLAN_Trunking/images/vlan5.png)

Một VLAN được xác định trên các switch bằng một ID VLAN. Mỗi cổng trên một switch sẽ được gán cho một hoặc nhiều VLAN ID, trường hợp không được chỉ định thì nó sẽ được chuyển tới một VLAN mặc định. Mỗi VLAN sẽ cung cấp quyền truy cập dữ liệu cho tất cả những thiết bị kết nối với cổng trên switch phù hợp với VLAN ID của nó.

ID VLAN sẽ được dịch sang thẻ VLAN bằng một thẻ 12 bit xác định tối đa 4096 VLAN trên mỗi miền chuyển mạch. IEEE sẽ chịu trách nhiệm gắn thẻ VLAN theo tiêu chuẩn 802.1Q. Switch sẽ thêm thẻ VLAN cho khung Ethernet. Với Static VLAN, switch sẽ chèn thẻ được liên kết với ID VLAN của cổng nhập. Riêng Dynamic VLAN, switch sẽ chèn thẻ được liên kết với ID của thiết bị đó hoặc loại lưu lượng mà nó tạo ra.

Các khung Ethernet được gắn thẻ sẽ chuyển tiếp về địa chỉ MAC đích của chúng (chỉ chuyển tiếp đến các cổng có liên kết VLAN). Lưu lượng quảng bá (broadcast), unicast, multicast đều được chuyển tiếp đến các cổng trong VLAN.

Đường trung kế kết nối (Trunk) giữa các switch nhận biết được VLAN nào trải dài trên switch. Trunk còn đóng vai trò truyền lưu lượng truy cập cho các VLAN được sử dụng ở hai phía đầu, cuối của nó. Khi một khung chạm đến switch đích thì thẻ VLAN sẽ bị xóa trước khi khung được truyền tới máy tính đích.

Spanning Tree Protocol (STP) là một giao thức được dùng để ngăn chặn sự lặp vòng giữa các switch trong mỗi miền lớp 2 (Ethernet). Mỗi VLAN sẽ chạy một STP riêng biệt, không phụ thuộc lẫn nhau. Nếu cấu trúc liên kết giữa nhiều VLAN giống nhau thì có thể chạy STP đa trường hợp để giảm chi phí STP.

## 2. Trunking

### 2.1. Trunking là gì?

Đường Trunk hay Trunking là một kỹ thuật kết nối các thiết bị mạng với nhau để tạo thành một mạng lớn hơn, đặc biệt trong các mạng LAN (Local Area Network) hoặc các mạng VLAN (Virtual Local Area Network). Đường trunk cho phép chuyển gói dữ liệu từ một VLAN này sang một VLAN khác trên cùng một đường truyền vật lý, điều này giúp tối ưu hóa việc sử dụng băng thông và giảm độ trễ trong mạng.
 
![vlan6](/QuyenNV/1.CCNA/VLAN_Trunking/images/vlan6.png)

Khi một cổng được cấu hình trunk, dữ liệu từ nhiều VLAN sẽ truyền qua cùng một đường truyền. Để phân biệt gói tin thuộc VLAN nào, người ta sử dụng các giao thức gắn thẻ (tagging). Có 2 chuẩn phổ biến là IEEE 802.1Q (DOT1Q) và ISL

### 2.2. Chuẩn IEEE 802.1Q (DOT1Q)

IEEE 802.1Q (hay DOT1Q) là tiêu chuẩn VLAN trunking do IEEE phát triển. Nó cho phép nhiều VLAN sử dụng chung một đường truyền vật lý giữa các thiết bị mạng (switch, router, firewall, ...).

Gói tin VLAN khi đi qua cổng trunk sẽ được gắn thẻ VLAN (VLAN Tagging) theo chuẩn 802.1Q.

![vlan7](/QuyenNV/1.CCNA/VLAN_Trunking/images/vlan7.png)

**Cấu trúc thẻ VLAN 802.1Q (4-byte tag field)**

- EtherType: sử dụng EtherType 0x8100 để cho biết đây là một khung 802.1Q.

- PRI: 3 bit, quy định độ ưu tiên của frame.

- Token Ring Encapsulation Flag: giúp chuyển đổi giữa mạng Ethernet và Token Ring.

- VLAN ID: 12 bit, dùng để xác định VLAN của frame.

**Cách xử lý frame**

Khi switch nhận được Frame có tag thông tin 802.1Q, nó sẻ tiến hành đọc thông tin này, xem frame này đến từ VLAN nào. Sau đó nó sẻ xử lí gở bỏ Tag trả lại frame đúng VLAN mà frame thuộc về. Thực chất Tag DOT1Q chỉ được tag trên đường trunk để phân biệt các frame của các VLAN khác nhau. Các End users không nhận biết được rằng frame được Tag và chuyển trên đường trunk. Trunking hoàn toàn transparent với các thiết bị đầu cuối này.

### 2.3. Chuẩn ISL (Inter-Switch Link) của Cisco

ISL (Inter-Switch Link) là giao thức trunking độc quyền của Cisco, được sử dụng để truyền nhiều VLAN qua một liên kết trunk giữa các thiết bị mạng của Cisco. ISL chỉ hoạt động trên thiết bị Cisco và không phải là tiêu chuẩn IEEE như 802.1Q.

- ISL encapsulation: ISL đóng gói toàn bộ frame Ethernet gốc bằng cách thêm một header 26-byte và một trailer 4-byte.

- ISL hỗ trợ tối đa 1024 VLANs, ít hơn so với 802.1Q (4094 VLANs).

![vlan8](/QuyenNV/1.CCNA/VLAN_Trunking/images/vlan8.png)

Cấu trúc Header ISL (30 byte): 

- DA (Destination address): 40 bit địa chỉ đích.

- Type: 4 bit mô tả của các loại frame: Ethernet (0000), Token Ring (0001), FDDI (0010) và ATM (0011).

- User: 4 bit để xác định các ưu tiên Ethernet.

- SA (Source address): 48 bit địa chỉ MAC nguồn của cổng truyền trên Switch.

- LEN (Length): 16 bit mô tả độ dài của frame Ethernet gốc.

- AAAA03: 24 bit, đây là một hằng số.

- HSA (High bits of source address): 3 byte đầu tiên của SA (ID của nhà sản xuất).

- VID: 15 bit, nhưng chỉ có 10 bit được sử dụng cho 1024 VLAN. Dùng để phân biệt các frame của các VLAN.

- BPDU (Bridge Protocol Data Unit): 1 bit Xác định frame có phải BPDU (Bridge Protocol Data Unit) không.

- INDX (index): 16 bit dùng để định danh một số port trunk trên switch.

- RES: 16 bit không sử dụng, để dành cho tương lai.

- Encapsulated Ethernet Frame: Frame Ethernet gốc (Original Ethernet Frame). ISL bọc toàn bộ frame Ethernet, giữ nguyên thông tin frame gốc.

- ISL Trailer: CRC (FCS - Frame Check Sequence - 4 byte): Kiểm tra lỗi frame sau khi được encapsulated.

### 2.4. Access port và Trunk port

![vlan9](/QuyenNV/1.CCNA/VLAN_Trunking/images/vlan9.png)

**Access port (Cổng truy nhập)**

- Một cổng trên Switch sẽ hoạt động trong chế độ cổng truy nhập (Access link) hoặc cổng trung kế (Trunk link).

- Trong chế độ cổng truy nhập, cổng chỉ thuộc một VLAN. Tất cả các máy tính cắm vào cổng này đều thuộc VLAN đó.

- Frame được gửi trên cổng truy nhập sẽ tuân theo chuẩn định dạng khung ethernet (802.3).

- Cổng truy nhập thường dùng khi cổng được kết nối đến máy trạm.

**Trunk port (Cổng trung kế)**

![vlan10](/QuyenNV/1.CCNA/VLAN_Trunking/images/vlan10.png)

- Cổng trung kế (Trunk port) là một kết nối vật lý và logic để hỗ trợ các VLAN trên các Switch liên kết với nhau.

- Cổng trung kế cho phép frame của nhiều VLAN có thể truyền trên đó. Một cổng trung kế không được gán cho một VLAN riêng biệt.

- Cổng trung kế thường được dùng để kết nối giữa các Switch hoặc giữa Switch và Router. Chính vì vậy cổng trung kế thường là cổng có băng thông lớn.

- Các VLAN được ghép kênh qua cổng trung kế. Để ghép kênh lưu lượng của các VLAN, một giao thức đặc biệt sẽ được sử dụng để đóng gói frame để thiết bị có thể xác định được nó thuộc VLAN nào. Chuẩn frame được sử dụng đó là 802.1Q hoặc ISL.

- Nhờ cổng trung kế mà một VLAN có thể được mở rộng ra toàn mạng.

- Chỉ cần một đường vật lý cho cả hai VLAN giữa hai Switch.

### 2.5. VTP (Vlan Trunking Protocol) 

VTP (Vlan Trunking Protocol) là giao thức hoạt động ở tầng liên kết dữ liệu trong mô hình OSI. VTP giúp cho việc cấu hình VLAN luôn đồng nhất khi thêm, xóa, sửa thông tin về VLAN trong hệ thống mạng.

**Hoạt động của VTP**

![vlan11](/QuyenNV/1.CCNA/VLAN_Trunking/images/vlan11.png)

VTP gửi thông điệp quảng bá qua VTP domain mỗi 5 phút hoặc khi có thay đổi về cấu hình VLAN.

Một thông điệp VTP bao gồm:

- Revision-number (số hiệu phiên bản VLAN).

- Tên VLAN (VLAN name).

- Số hiệu VLAN (VLAN ID).

Khi cấu hình VTP Server, nó sẽ gửi thông tin VLAN đến tất cả các switch trong cùng VTP domain để đồng bộ VLAN.

Revision-number là tham số quan trọng:

- Mỗi khi VTP Server thay đổi thông tin VLAN, nó tăng revision-number lên 1.

- Switch nhận thông điệp VTP có revision-number lớn hơn sẽ cập nhật cấu hình VLAN mới nhất.

**Các chế độ hoạt động của VTP**

![vlan12](/QuyenNV/1.CCNA/VLAN_Trunking/images/vlan12.png)

Server Mode:

- Switch hoạt động như máy chủ VTP, có quyền tạo, xóa, chỉnh sửa VLAN.

- VLAN thay đổi trên switch server sẽ được đồng bộ đến các switch khác trong cùng VTP Domain.

- Mặc định, mọi switch Cisco đều ở chế độ này.

Client Mode:

- Không thể tạo, xóa hoặc chỉnh sửa VLAN.

- Nhận thông tin VLAN từ switch VTP Server và áp dụng cho các cổng trunk.

Transparent Mode:

- Không tham gia vào quá trình đồng bộ VLAN.

- Chỉ chuyển tiếp thông điệp VTP đến các switch khác trong mạng.

- Có thể tạo VLAN cục bộ nhưng không chia sẻ với switch khác.

## 3. Một số thiết bị khác

### 3.1 Router (Bộ định tuyến)

![vlan14](/QuyenNV/1.CCNA/VLAN_Trunking/images/vlan14.png)

#### 3.1.1. Khái niệm

- Router là thiết bị mạng hoạt động ở Layer 3 (Network Layer) của mô hình OSI.

- Dùng để kết nối các mạng khác nhau và định tuyến gói tin dựa trên địa chỉ IP.

- Router có thể kết nối mạng LAN với Internet hoặc kết nối nhiều mạng LAN lại với nhau.

- Hỗ trợ các giao thức định tuyến OSPF, EIGRP, BGP, RIP, cũng như các chức năng mạng nâng cao như:

  - NAT (Network Address Translation): Chuyển đổi địa chỉ IP riêng thành địa chỉ IP công cộng.

  - DHCP (Dynamic Host Configuration Protocol): Cấp phát địa chỉ IP tự động cho thiết bị trong mạng.

  - QoS (Quality of Service): Quản lý băng thông và ưu tiên lưu lượng quan trọng.

  - ACLs (Access Control Lists): Kiểm soát lưu lượng và bảo mật

#### 3.1.2. Cách hoạt động

- Khi nhận được gói tin, router sẽ kiểm tra địa chỉ IP đích.

- Dựa vào bảng định tuyến (Routing Table), router tìm đường đi tốt nhất để gửi gói tin.

- Router có thể sử dụng:

  - Static Routing (Định tuyến tĩnh): Quản trị viên cấu hình đường đi cố định.

  - Dynamic Routing (Định tuyến động): Router tự động học và cập nhật đường đi tối ưu dựa trên các giao thức định tuyến.

#### 3.1.3. Ưu và nhược điểm

**Ưu điểm**:

- Kết nối mạng LAN với Internet hoặc nhiều mạng LAN khác nhau.

- Tối ưu hóa lưu lượng, giảm nghẽn mạng.

- Hỗ trợ nhiều tính năng bảo mật và quản lý mạng.

**Nhược điểm**:

- Chậm hơn switch khi xử lý lưu lượng nội bộ trong LAN.

- Cấu hình phức tạp hơn.

- Chi phí cao hơn switch.

### 3.2. Switch – L2 và L3

#### 3.2.1. Switch Layer 2 (L2)

![vlan15](/QuyenNV/1.CCNA/VLAN_Trunking/images/vlan15.png)

- Switch L2 hoạt động ở Layer 2 (Data Link Layer).

- Chuyển tiếp gói tin dựa trên địa chỉ MAC.

- Hỗ trợ tính năng VLAN (Virtual LAN) giúp chia mạng thành nhiều phân đoạn nhỏ.

**Cách hoạt động**

- Khi nhận một frame, switch kiểm tra địa chỉ MAC đích.

- Nếu đã biết địa chỉ MAC này trong MAC Address Table, switch sẽ gửi frame trực tiếp.

- Nếu chưa biết, switch sẽ gửi frame đến tất cả các cổng (trừ cổng nhận frame).

- Khi frame đến đúng thiết bị, switch học địa chỉ MAC mới vào bảng MAC để lần sau gửi nhanh hơn.

**Ưu và nhược điểm của Switch L2**

**Ưu điểm**:

- Tốc độ cao, phù hợp với LAN nội bộ.

- Giảm xung đột mạng (collision domain).

- Hỗ trợ VLAN để chia nhỏ mạng.

**Nhược điểm**:

- Không thể định tuyến giữa các VLAN.

- Không hỗ trợ IP hoặc định tuyến.

#### 3.2.2. Switch Layer 3 (L3)

![vlan16](/QuyenNV/1.CCNA/VLAN_Trunking/images/vlan16.png)

- Switch L3 có thể hoạt động ở cả Layer 2 và Layer 3.

- Hỗ trợ định tuyến giữa VLAN (Inter-VLAN Routing) mà không cần router.

- Hỗ trợ giao thức định tuyến như OSPF, EIGRP, RIP.

**Cách hoạt động**

- Khi nhận gói tin giữa các VLAN, switch L3 kiểm tra địa chỉ IP đích và thực hiện định tuyến nội bộ.

- Hỗ trợ tính năng Routing Table giúp chuyển tiếp gói tin nhanh chóng mà không cần router.

**Ưu và nhược điểm của Switch L3**

**Ưu điểm**:

- Định tuyến nhanh hơn router trong mạng LAN.

- Hỗ trợ nhiều VLAN mà không cần router riêng.

- Tăng hiệu suất mạng.

**Nhược điểm**:

- Giá thành cao hơn switch L2.

- Không hỗ trợ các tính năng WAN như NAT, VPN.

### 3.3. Firewall (Tường lửa)

#### 3.3.1. Khái niệm

- Firewall là thiết bị bảo mật mạng, kiểm soát lưu lượng vào/ra dựa trên chính sách bảo mật.

- Hoạt động ở Layer 3 - Layer 7, giúp ngăn chặn các cuộc tấn công mạng.

#### 3.3.2. Các loại Firewall

**Packet Filtering Firewall (L3)**

- Kiểm tra gói tin dựa trên địa chỉ IP, port, và protocol.

- Chỉ cho phép hoặc chặn gói tin nhưng không kiểm tra trạng thái kết nối.

**Stateful Firewall (L4)**

- Theo dõi trạng thái của kết nối TCP (handshake, session).

- Kiểm soát lưu lượng hiệu quả hơn packet filtering firewall.

**Application Firewall (L7)**

- Kiểm tra nội dung gói tin ở cấp độ ứng dụng (HTTP, FTP, SMTP).

- Phát hiện và chặn tấn công SQL Injection, XSS.

#### 3.3.3. Ưu và nhược điểm

**Ưu điểm**:

- Bảo vệ chống lại tấn công mạng.

- Kiểm soát chi tiết lưu lượng mạng.

- Hỗ trợ VPN, IDS/IPS.

**Nhược điểm**:

- Cấu hình phức tạp.

- Giảm hiệu suất mạng nếu xử lý quá nhiều gói tin.

### 3.4. Hub

![vlan17](/QuyenNV/1.CCNA/VLAN_Trunking/images/vlan17.png)

#### 3.4.1. Khái niệm

- Hub hoạt động ở Layer 1 (Physical Layer).

- Chỉ đơn giản phát gói tin đến tất cả các cổng.

- Không có khả năng phân biệt địa chỉ MAC hay IP.

#### 3.4.2. Cách hoạt động

- Khi một thiết bị gửi dữ liệu, hub phát bản sao đến tất cả các thiết bị khác.

- Dẫn đến xung đột dữ liệu (collision) khi có nhiều thiết bị gửi cùng lúc.

#### 3.4.3. Ưu và nhược điểm

**Ưu điểm**:

- Rẻ, dễ sử dụng.

- Không cần cấu hình.

**Nhược điểm**:

- Hiệu suất thấp, gây xung đột.

- Không hỗ trợ VLAN hay bảo mật.

---

### 3.5. So sánh Router, Switch (L2/L3), Firewall, và Hub

| Thiết bị | Layer | Chức năng chính | Định tuyến IP | Hỗ trợ VLAN | Bảo mật |
|----------|--------|------------------|---------------|-------------|---------|
| **Router** | L3 | Kết nối mạng khác nhau | Có | Có (Inter-VLAN) | Có (ACL, NAT) |
| **Switch L2** | L2 | Kết nối thiết bị trong LAN | Không | Có | Không |
| **Switch L3** | L2/L3 | Kết nối & định tuyến VLAN | Có | Có | Có (ACL) |
| **Firewall** | L3 - L7 | Bảo vệ mạng, kiểm soát lưu lượng | Có | Có | Cao |
| **Hub** | L1 | Phát gói tin đến tất cả các thiết bị | Không | Không | Không |
