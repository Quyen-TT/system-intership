# Phân tích gói tin sử dụng WireShark và TCPdump

## Wirshark

Các gói tin DHCP mà WireShark bắt được:

![anh4](/QuyenNV/DHCP/images/anh4.png)

### 1. DHCP Discover

![anh5](/QuyenNV/DHCP/images/anh5.png)

![anh6](/QuyenNV/DHCP/images/anh6.png)

**Tầng 2: Ethernet II**

- Src (Nguồn): 00:0c:29:c8:21:9b (Địa chỉ MAC máy khách).

- Dst (Đích): Broadcast (ff:ff:ff:ff:ff:ff).

**Tầng 3: Internet Protocol Version 4 (IPv4)**

- Src IP: 0.0.0.0 -> Máy khách chưa có IP.

- Dst IP: 255.255.255.255 -> Broadcast toàn mạng để tìm DHCP server.

**Tầng 4: UDP**

- Src port: 68 -> cổng của DHCP client

- Dst port: 67 -> cổng của DHCP server

**Bootstrap Protocol (DHCP Discover)**

- Message type: Boot Request (1) -> Gói tin từ client gửi đi → yêu cầu cấp IP.

### 2. DHCP Offer

![anh7](/QuyenNV/DHCP/images/anh7.png)

![anh8](/QuyenNV/DHCP/images/anh8.png)

**Tầng 2: Ethernet II**

- Src: 00:0c:29:5e:51:6c -> MAC của DHCP Server

- Dst: 00:0c:29:c8:21:9b ->  MAC của Client

**Tầng 3: Internet Protocol Version 4 (IPv4)**

- Src IP: 192.168.91.100 -> Địa chỉ của DHCP server

- Dst IP: 192.168.91.102 -> IP được đề xuất cho client

**Tầng 4: UDP**

- Src port: 67 (DHCP server)

- Dst port: 68 (DHCP client)

**Bootstrap Protocol (Offer)**

- Message type: Boot Reply (2) -> Phản hồi từ server

- Your (client) IP address: 192.168.91.102 -> IP được cấp phát cho client

- IP Address lease time: thời gian thuê IP

- subnet mask, router, dns,...

### 3. DHCP Request

![anh9](/QuyenNV/DHCP/images/anh9.png)

![anh10](/QuyenNV/DHCP/images/anh10.png)

**Tầng 2: Ethernet II**

- Src MAC: 00:0c:29:c8:21:9b -> MAC của máy client

- Dst MAC: ff:ff:ff:ff:ff:ff -> Broadcast đến tất cả

**Tầng 3: Internet Protocol Version 4 (IPv4)**

- Src IP: 0.0.0.0 -> Vì client chưa có IP

- Dst IP: 255.255.255.255 -> Gửi broadcast để DHCP server nào gửi Offer biết là được chọn

**Tầng 4: UDP**

- Src port: 68 -> cổng của DHCP client

- Dst port: 67 -> cổng của DHCP server

**Bootstrap Protocol (Request)**

- Message Type: Request -> DHCP Client chọn một Offer từ server (gói thứ 2) và gửi lại yêu cầu xác nhận sử dụng IP đó.

- Các thông tin quan trọng:

    - Requested IP Address: IP mà client muốn nhận (do server đề xuất trước đó).

    - Parameter Request List: Client yêu cầu các tùy chọn cấu hình từ server (DNS, Gateway, Lease time...).

### 4. DHCP ACK

![anh11](/QuyenNV/DHCP/images/anh11.png)

![anh12](/QuyenNV/DHCP/images/anh12.png)

**Tầng 2: Ethernet II**

- Src MAC: 00:0c:29:52:51:6c -> MAC của DHCP server

- Dst MAC: 00:0c:29:c8:21:9b -> MAC của client

**Tầng 3: Internet Protocol Version 4 (IPv4)**

Src IP: 192.168.91.100 -> IP của server

Dst IP: 192.168.91.102 -> IP được gán cho client

**Tầng 4: UDP**

- Src port: 68 -> cổng của DHCP client

- Dst port: 67 -> cổng của DHCP server

**Bootstrap Protocol (ACK)**

- Message Type: ACK -> DHCP server xác nhận và chính thức cấp phát IP được client chọn trong gói Request.

- Các DHCP Options:

    - IP lease time.

    - Default gateway.
    
    - DNS servers.

    - Subnet mask.

## TCPdump

Sử dụng câu lệnh:

    sudo tcpdump -i ens33 port 67 or port 68 -n -vv

cấp phát lại địa chỉ IP mới:

    sudo dhclient -r ens160
    sudo dhclient -v ens160

### 1. DHCP Discover

![anh13](/QuyenNV/DHCP/images/anh13.png)

### 2. DHCP Offer

![anh14](/QuyenNV/DHCP/images/anh14.png)

### 3. DHCP Request

![anh15](/QuyenNV/DHCP/images/anh15.png)

### 4. DHCP ACK

![anh16](/QuyenNV/DHCP/images/anh16.png)

