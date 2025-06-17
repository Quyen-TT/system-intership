![lab1](/QuyenNV/CCNA/Routing/images/lab1.png)

# Cấu hình trên Router1

    enable
    configure terminal
    hostname R1
    interface FastEthernet0/0
    ip address 192.168.2.1 255.255.255.0
    no shutdown
    interface FastEthernet1/0
    ip address 192.168.1.1 255.255.255.0
    no shutdown
    exit

# Cấu hình trên Router2

    enable
    configure terminal
    hostname R2
    interface FastEthernet0/0
    ip address 192.168.1.2 255.255.255.0
    no shutdown
    interface FastEthernet1/0
    ip address 192.168.3.1 255.255.255.0
    no shutdown
    exit

## Bảng định tuyến trên R1

![lab2](/QuyenNV/CCNA/Routing/images/lab2.png)

## Bảng định tuyến trên R2

![lab3](/QuyenNV/CCNA/Routing/images/lab3.png)

# Cấu hình trên PC1

    IP Address: 192.168.2.10
    Subnet Mask: 255.255.255.0
    Default Gateway: 192.168.2.1

# Cấu hình trên PC2

    IP Address: 192.168.3.10
    Subnet Mask: 255.255.255.0
    Default Gateway: 192.168.3.1

# Cấu hình sử dụng định tuyến tĩnh (Static Route)

Câu lệnh: 

    Router(config)# ip route (network-address) (subnet-mask) (next-hop ip address/ exit interface)

## Trên R1 , thêm tuyến đường đến 192.168.3.0/24:

    ip route 192.168.3.0 255.255.255.0 192.168.1.2

## Trên R2, thêm tuyến đường đến 192.168.2.0/24:

    ip route 192.168.2.0 255.255.255.0 192.168.1.1

# Ping từ PC1 đến PC2

![lab4](/QuyenNV/CCNA/Routing/images/lab4.png)

# Ping từ PC2 đến PC1

![lab5](/QuyenNV/CCNA/Routing/images/lab5.png)

# Quá trình truyền dữ liệu giữa PC1 và PC2 

![lab6](/QuyenNV/CCNA/Routing/images/lab6.png)