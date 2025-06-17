# Cấu hình chia VLAN trên Switch

![lab1](/QuyenNV/CCNA/VLAN_Trunking/images/lab1.png)

## Các bước thực hiện

### 1. Tạo các VLAN10, VLAN11, VLAN12

- Truy cập vào Cisco Packet Tracer -> Chọn Switch -> Chọn CLI.

- Thực hiện các câu lệnh sau: 

```
Switch>enable  
Switch#configure terminal  

Switch(config)#vlan 10  
Switch(config-vlan)#name VLAN10  
Switch(config-vlan)#exit  

Switch(config)#vlan 11  
Switch(config-vlan)#name VLAN11  
Switch(config-vlan)#exit  

Switch(config)#vlan 12  
Switch(config-vlan)#name VLAN12  
 Switch(config-vlan)#exit  
```

- Kiểm tra lại VLAN vừa tạo:

![lab2](/QuyenNV/CCNA/VLAN_Trunking/images/lab2.png)

### 2. Gán các port vào VLAN đã định trước

    Switch>enable
    Switch#configure terminal

**Cổng Fa0/1 và Fa0/2 vào VLAN10 (PC1, PC2):**

    Switch(config)#interface fastEthernet 0/1
    Switch(config-if)#switchport access vlan 10
    Switch(config-if)#exit

    Switch(config)#interface fastEthernet 0/2
    Switch(config-if)#switchport access vlan 10
    Switch(config-if)#exit

**Cổng Fa0/11 và Fa0/12 vào VLAN11 (PC3, PC4):**

    Switch(config)#interface fastEthernet 0/11
    Switch(config-if)#switchport access vlan 11
    Switch(config-if)#exit

    Switch(config)#interface fastEthernet 0/12
    Switch(config-if)#switchport access vlan 11
    Switch(config-if)#exit

**Cổng Fa0/21 và Fa0/22 vào VLAN10 (PC5, PC6):**

    Switch(config)#interface fastEthernet 0/21
    Switch(config-if)#switchport access vlan 12
    Switch(config-if)#exit

    Switch(config)#interface fastEthernet 0/22
    Switch(config-if)#switchport access vlan 12
    Switch(config-if)#end  

Kiểm tra các port gán đúng vlan chưa:

    Switch#show vlan

![lab3](/QuyenNV/CCNA/VLAN_Trunking/images/lab3.png)

### 3. Ping giữa các máy 

Nhập IP tĩnh cho các PC: Chọn PC -> Desktop -> IP Configuration -> Nhập IP tương ứng

Chọn PC1 -> Desktop -> Command Prompt

Tiến hành ping giữa các máy:

![lab4](/QuyenNV/CCNA/VLAN_Trunking/images/lab4.png)

Làm tương tự với các PC khác: 

![lab5](/QuyenNV/CCNA/VLAN_Trunking/images/lab5.png)

# Cấu hình VTP domain

**Sơ đồ lab:**

![lab6](/QuyenNV/CCNA/VLAN_Trunking/images/lab6.png)

**Quy hoạch VLAN:**

VLAN10 : 192.168.10.0/24  
VLAN20 : 192.168.20.0/24

![lab7](/QuyenNV/CCNA/VLAN_Trunking/images/lab7.png)

**Quy hoạch IP và kết nối:**

![lab8](/QuyenNV/CCNA/VLAN_Trunking/images/lab8.png)

## Các bước thực hiện 

### 1. Đặt IP cho các PC theo phân hoạch

Chọn PC -> Desktop -> IP Configuration -> Nhập IP tương ứng

### 2. Thiết lập các VLAN trên 2 SW

**Trên SW 1**

Đặt tên:

    Switch>enable 
    Switch#configure terminal 
    Switch(config)#hostname SW1
    SW1(config)#

Tạo 2 VLAN10 và VLAN20:

    SW1(config)#vlan 10
    SW1(config-vlan)#name VLAN10
    SW1(config-vlan)#exit

    SW1(config)#vlan 20
    SW1(config-vlan)#name VLAN20
    SW1(config-vlan)#exit

    SW1(config)#

Gán các port vào đúng các VLAN định sẵn:

    SW1(config)#interface fastEthernet 0/10
    SW1(config-if)#switchport access vlan 10
    SW1(config-if)#exit

    SW1(config)#interface fastEthernet 0/11
    SW1(config-if)#switchport access vlan 10
    SW1(config-if)#exit

    SW1(config)#interface fastEthernet 0/20
    SW1(config-if)#switchport access vlan 20
    SW1(config-if)#exit

    SW1(config)#exit

Kiểm tra lại:

    SW1#show vlan

![lab9](/QuyenNV/CCNA/VLAN_Trunking/images/lab9.png)

**Trên SW2**

Đặt tên:

    Switch>enable 
    Switch#configure terminal 
    Switch(config)#hostname SW2
    SW2(config)#

Tạo 2 VLAN10 và VLAN20:

    SW2(config)#vlan 10
    SW2(config-vlan)#name VLAN10
    SW2(config-vlan)#exit

    SW2(config)#vlan 20
    SW2(config-vlan)#name VLAN20
    SW2(config-vlan)#exit

    SW2(config)#

Gán các port vào đúng các VLAN định sẵn:

    SW2(config)#interface fastEthernet 0/10
    SW2(config-if)#switchport access vlan 10
    SW2(config-if)#exit

    SW2(config)#interface fastEthernet 0/20
    SW2(config-if)#switchport access vlan 20
    SW2(config-if)#exit

    SW2(config)#exit

Kiểm tra lại:

    SW2#show vlan

![lab10](/QuyenNV/CCNA/VLAN_Trunking/images/lab10.png)

### 3. Cấu hình VTP

**Đặt IP cho các interface VLAN trên 2 SW**

Đặt địa chỉ IP cho interface VLAN10 của SW1 là 192.168.10.1 và VLAN20 là 192.168.20.1

    SW1#configure terminal 
    SW1(config)#interface vlan 10
    SW1(config-if)#
    SW1(config-if)#ip address 192.168.10.1 255.255.255.0
    SW1(config-if)#no shutdown
    SW1(config-if)#exit
    SW1(config)#

    SW1(config)#interface vlan 20
    SW1(config-if)#ip address 192.168.20.1 255.255.255.0
    SW1(config-if)#no shutdown 
    SW1(config-if)#exit 

    SW1(config)#exit
    SW1#

Đặt địa chỉ IP cho interface VLAN10 của SW2 là 192.168.10.2 và VLAN20 là 192.168.20.2

    SW2#configure terminal 
    SW2(config)#interface vlan 10
    SW2(config-if)#
    SW2(config-if)#ip address 192.168.10.2 255.255.255.0
    SW2(config-if)#no shutdown
    SW2(config-if)#exit
    SW2(config)#

    SW2(config)#interface vlan 20
    SW2(config-if)#ip address 192.168.20.2 255.255.255.0
    SW2(config-if)#no shutdown 
    SW2(config-if)#exit 

    SW2(config)#exit
    SW2#

**Thiết lập VTP Server và VTP Client**

Mặc định thì Catalyst switch sẽ được cấu hình làm VTP Server. Giờ ta sẽ thiết lập:

- Switch 1: VTP Server

- Switch 2: VTP CLient.

Ngoài ra, ta đặt

- VTP domain: NH

- VTP password: nhanhoa2020.

**Trên SW1**

    SSW1>enable
    SW1#configure terminal
    SW1(config)#vtp mode server
    SW1(config)#vtp domain NH
    SW1(config)#vtp password nhanhoa2020
    SW1(config)#exit
    SW1#

**Trên SW2**

    SW2>enable
    SW2#configure terminal
    SW2(config)#vtp mode client
    SW2(config)#vtp domain NH
    SW2(config)#vtp password nhanhoa2020
    SW2(config)#exit
    SW2#

**Tạo đường trunk từ SW1 đến SW2**

Ta sẽ bật trunking trên các port nối giữa 2 switch là Fa0/1 trên SW1 và Fa0/1 trên SW2.

**Trên SW1**

    SW1#configure terminal 
    SW1(config)#interface fastEthernet 0/1
    SW1(config-if)#switchport mode trunk 
    SW1(config-if)#end
    SW1#

**Trên SW2**

    SW2#configure terminal 
    SW2(config)#interface fastEthernet 0/1
    SW2(config-if)#switchport mode trunk 
    SW2(config-if)#end
    SW2#

### 4. Các lệnh kiểm tra sau khi cấu hình xong

    SW# show vtp status

![lab11](/QuyenNV/CCNA/VLAN_Trunking/images/lab11.png)

![lab12](/QuyenNV/CCNA/VLAN_Trunking/images/lab12.png)

    SW# show vtp pasword

![lab13](/QuyenNV/CCNA/VLAN_Trunking/images/lab13.png)

![lab14](/QuyenNV/CCNA/VLAN_Trunking/images/lab14.png)

    SW# show vlan

![lab15](/QuyenNV/CCNA/VLAN_Trunking/images/lab15.png)

![lab16](/QuyenNV/CCNA/VLAN_Trunking/images/lab16.png)

    SW# show interfaces trunk

![lab17](/QuyenNV/CCNA/VLAN_Trunking/images/lab17.png)

![lab18](/QuyenNV/CCNA/VLAN_Trunking/images/lab18.png)