# Bài tập chia subnet

## 4.6.1. Cho mạng và số bit mượn. Giả sử có hỗ trợ subnet zero. Hãy xác định :
- Số subnet có thể có.
- Số host/subnet.
- Với mỗi subnet, hãy xác định: địa chỉ mạng, địa chỉ host đầu, địa chỉ host cuối,
địa chỉ broadcast (nếu số lượng mạng quá nhiều chỉ cần ghi ra một vài mạng đầu
và mạng cuối cùng), subnet mask và số prefix

### a, 192.168.2.0/24 mượn 5 bit. 

- số bit mượn là 5 => số bit mạng là 24 + 5 = 29
- số bit host còn lại là 32 - 29 = 3
- số subnet có thể: 2^5 = 32
- số host/subnet: 2^3 - 2 = 6
- các địa chỉ mạng sẽ có octet bị chia cắt (octet thứ 4) là bội số của 8
- liệt kê các mạng như sau:

192.168.2.0/29 : địa chỉ mạng  
192.168.2.1/29 :địa chỉ host đầu  
192.168.2.6/29 : địa chỉ host cuối  
192.168.2.7/29 : địa chỉ broadcast  

***

192.168.2.8/29 : địa chỉ mạng  
192.168.2.9/29 : địa chỉ host đầu  
192.168.2.14/29 : địa chỉ host cuối  
192.168.2.15/29 : địa chỉ host broadcast  

***
. . .

***

192.168.2.248/29 : địa chỉ mạng  
192.168.2.249/29 : địa chỉ host đầu  
192.168.2.254/29 : địa chỉ host cuối  
192.168.2.255/29 : địa chỉ broadcast  

- subnet mask được sử dụng là 255.255.255.248
- số prefix là 29

### b, 192.168.12.0/24 mượn 3 bit.

- số bit mượn là 3 => số bit mạng là 24 + 3 = 27
- số bit host còn lại là 32 - 27 = 5
- số subnet có thể: 2^3 = 8
- số host/subnet: 2^5 - 2 = 30
- các địa chỉ mạng sẽ có octet bị chia cắt (octet thứ 4) là bội số của 32
- Liệt kê các mạng như sau:

172.16.2.0/26 : địa chỉ mạng
172.16.2.1/26 : địa chỉ host đầu
172.16.2.62/26 : địa chỉ host cuối
172.16.2.63/26 : địa chỉ broadcast

***  
...

***

172.16.2.192/26 : địa chỉ mạng
172.16.2.193/26 : địa chỉ host đầu
172.16.2.254/26 : địa chỉ host cuối
172.16.2.255/26 : địa chỉ broadcast

- subnet mask được sử dụng là 255.255.255.192
- số prefix là 26

### c, 172.16.2.0/24 mượn 2 bit

- số bit mượn là 2 => số bit mạng là 24 + 2 = 26
- số bit host còn lại là 32 - 26 = 6 
- số subnet có thể: 2^2 = 4
- số host/subnet: 2^6 - 2 = 62
- các địa chỉ mạng sẽ có octet bị chia cắt (octet thứ 4) là bội số của 64
- Liệt kê các mạng như sau:

172.16.2.0/26 : địa chỉ mạng  
172.16.2.1/26 : địa chỉ host đầu  
172.16.2.62/26 :địa chỉ host cuối  
172.16.2.63/26 : địa chỉ broadcast  

***

172.16.2.64/26 : địa chỉ mạng  
172.16.2.65/26 : địa chỉ host đầu  
172.16.2.126/26 :địa chỉ host cuối  
172.16.2.127/26 : địa chỉ broadcast  

***

. . .

***

172.16.2.192/26 : địa chỉ mạng  
172.16.2.193/26 : địa chỉ host đầu  
172.16.2.254/26 : địa chỉ host cuối  
172.16.2.255/26 : địa chỉ broadcast  

- subnet mask được sử dụng là 255.255.224.0
- số prefix là 19

### d, 172.16.0.0/16 mượn 3 bit

- số bit mượn là 3 => số bit mạng là 16 + 3 = 19
- số bit host còn lại là 32 - 19 = 13
- số subnet có thể: 2^3 = 8
- số host/subnet: 2^13 - 2
- các địa chỉ mạng sẽ có octet bị chia cắt (octet thứ 3) là bội số của 32
- Liệt kê các mạng như sau: 

172.16.0.0/19 : địa chỉ mạng  
172.16.0.1/19 : địa chỉ host đầu  
172.16.31.254/19 : địa chỉ host cuối  
172.16.31.255/19 : địa chỉ broadcast  

***

172.16.32.0/19 : địa chỉ mạng  
172.16.32.1/19 : địa chỉ host đầu  
172.16.63.254/19 : địa chỉ host cuối  
172.16.63.255/19 : địa chỉ broadcast  

***

...

***

172.16.224.0/19 : địa chỉ mạng  
172.16.224.1/19 : địa chỉ host đầu  
172.16.255.254/19 : địa chỉ host cuối  
172.16.255.255/19 : địa chỉ broadcast  

- subnet mask được sử dụng là 255.255.224.0
- số prefix là 19

### e, 172.16.0.0/16 mượn 12 bit.

- số bit mượn là 12 => số bit mạng là 16 + 12 = 28
- số bit host còn lại là 32 - 28 = 4
- số subnet có thể: 2^12 = 4096
- số host/subnet: 2^4 - 2 = 14
- các địa chỉ mạng sẽ có octet bị chia cắt (octet thứ 4 ) là bội số của 16
- Liệt kê các mạng như sau:

172.16.0.0/28 : địa chỉ mạng  
172.16.0.1/28 : địa chỉ host đầu  
172.16.0.14/28 : địa chỉ host cuối  
172.16.0.15/28 : địa chỉ broadcast  

***

172.16.0.16/28 : địa chỉ mạng  
172.16.0.17/28 : địa chỉ host đầu  
172.16.0.30/28 : địa chỉ host cuối  
172.16.0.31/28 : địa chỉ broadcast  

***

. . .

***

172.16.0.240/28 : địa chỉ mạng  
172.16.0.241/28 : địa chỉ host đầu  
172.16.0.254/28 : địa chỉ host cuối  
172.16.0.255/28 : địa chỉ broadcast  

***

172.16.1.0/28 : địa chỉ mạng  
172.16.1.1/28 : địa chỉ host đầu  
172.16.1.14/28 : địa chỉ host cuối  
172.16.1.15/28 : địa chỉ broadcast  

***

. . .

***

172.16.255.240/28 : địa chỉ mạng  
172.16.255.241/28 : địa chỉ host đầu  
172.16.255.254/28 : địa chỉ host cuối  
172.16.255.255/28 : địa chỉ broadcast  

### f, 10.0.0.0/8 mượn 5 bit.

- số bit mượn là 5 => số bit mạng là 5 + 8 = 13
- số bit host còn lại là 32 - 13 = 19
- số subnet có thể: 2^5 = 32
- số host/subnet: 2^19 - 2
- Các địa chỉ mạng sẽ có octet bị chia cắt (octet thứ 2) là bội số của 8
- Liệt kê các mạng như sau:

10.0.0.0/13 : địa chỉ mạng  
10.0.0.1/13 : địa chỉ host đầu  
10.7.255.254/13 : địa chỉ host cuối  
10.7.255.255/13 : địa chỉ broadcast  

***

10.8.0.0/13 : địa chỉ mạng  
10.8.0.1/13 : địa chỉ host đầu  
10.8.255.254/13 : địa chỉ host cuối  
10.8.255.255/13 : địa chỉ broadcast  

***

. . .

***

10.248.0.0/13 -> địa chỉ mạng  
10.248.0.1/13 -> địa chỉ host đầu  
10.255.255.254/13 -> địa chỉ host cuối  
10.255.255.255/13 -> địa chỉ broadcast  

- địa chỉ subnet mask là 255.248.0.0
- số prefix là 13

### g, 10.0.0.0/8 mượn 10 bit.

- số bit mượn là 10, số bit mạng là 10 + 8 = 18
- số bit host còn lại là 32 - 18 = 14
- số subnet có thể: 2^10 = 1024
- số host/subnet: 2^14 - 2
- các địa chỉ mạng sẽ có octet bị chia cắt (octet thứ 3) là bội số của 64
- Liệt kê các mạng như sau:

10.0.0.0/18 : địa chỉ mạng  
10.0.0.1/18 : địa chỉ host đầu  
10.0.63.254/18 : địa chỉ host cuối  
10.0.63.255/18 : địa chỉ broadcast  

***

...

***

10.255.192.0/18 : địa chỉ mạng  
10.255.192.1/18 : địa chỉ host đầu  
10.255.255.254/18 : địa chỉ host cuối  
10.255.255.255/18 : địa chỉ broadcast  

- địa chỉ subnet mask là 255.255.192.0
- số prefix là 18

### h, 10.0.0.0/8 mượn 18 bit.

- số bit mượn là 18, số bit mạng là 18 + 8 = 26
- số bit host còn lại là 32 - 26 = 6
- số subnet có thể: 2^18
- số host/subnet: 2^6 - 2 = 62
- các địa chỉ mạng sẽ có octet bị chia cắt (octet thứ 4) là bội số của 64
- Liệt kê các mạng như sau:

10.0.0.0/24: địa chỉ mạng  
10.0.0.1/24: địa chỉ host đầu  
10.0.0.62/24 : địa chỉ host cuối  
10.0.0.63/24: địa chỉ broadcast  

***

10.0.0.64/24: địa chỉ mạng   
10.0.0.65/24: địa chỉ host đầu  
10.0.0.126/24 : địa chỉ host cuối  
10.0.0.127/24: địa chỉ broadcast  

***

. . .

***

10.0.0.192/24: địa chỉ mạng  
10.0.0.193/24: địa chỉ host đầu  
10.0.0.254/24 : địa chỉ host cuối  
10.0.0.255/24: địa chỉ broadcast  

***

. . .

***

10.255.255.192/24: địa chỉ mạng  
10.255.255.193/24: địa chỉ host đầu  
10.255.255.254/24 : địa chỉ host cuối  
10.255.255.255/24: địa chỉ broadcast  

- địa chỉ subnet mask là 255.255.192.0 
- số prefix là 26

## 4.6.2. Cho mạng 172.16.5.0/24. Hãy chia nhỏ sao cho phù hợp với sơ đồ sau:

![Ảnh 10](/QuyenNV/CCNA/IPv4/images/anh10.png)

Đầu tiên , xét mạng nhiều host nhất: 78 host, ta phải xem mượn bao nhiêu bit thì đủ cho mạng này. Ta giải hệ:  

- 2^m - 2 ≥ 79  
- m + n = 8 (mượn bit ở octet thứ 4). Với m: số bit host, n: số bit mượn  

Ta được m = 7, n = 1. Vậy ta mượn 1 bit và dành mạng 172.16.5.0/25 để gán cho mạng có 78 host. Mỗi mạng /25 có 2^7 – 2 = 126 host => đáp ứng đủ cho mạng 78 host.

Tiếp đó ta xét đến mạng có 50 host,  ta xem xem mượn bao nhiêu bit là phù hợp:

- 2^m – 2 ≥ 51
- m + n = 8 (mượn bit ở octet thứ 4). Với m: số bit host, n: số bit mượn

Ta được m = 6, n = 2. Vậy ta mượn 2 bit, mạng 172.16.5.0/24 được chia thành 4 mạng 172.16.5.0/26, 172.16.5.64/26, 172.16.5.128/26 và 172.16.5.192/26. Tuy nhiên hai dải địa chỉ của hai mạng 172.16.5.0/26 và 172.16.5.64/26 đã được giành cho mạng 78 host. Do đó ta chỉ có thể lấy từ mạng để gán 172.16.5.128/26 cho mạng 50 host. Ở đây ta lấy mạng 172.16.5.128/26 gán cho mạng 50 host.

Tiếp đó ta xét đến mạng có 20 host,  ta xem xem mượn bao nhiêu bit là phù hợp:

- 2^m – 2 ≥ 21
- m + n = 8 (mượn bit ở octet thứ 4). Với m: số bit host, n: số bit mượn

Ta được m = 5, n = 3. Vậy ta mượn 3 bit, mạng 172.16.5.0/24 được chia thành 8 mạng 172.16.5.0/27, 172.16.5.32/27, 172.16.5.64/27 và 172.16.5.96/27, 172.16.5.128/27, 172.16.5.160/27, 172.16.5.192/27, 172.16.5.224/27. Tuy nhiên các dải địa chỉ của các mạng 172.16.5.0/27 , ..., 172.16.5.160/27 đã được giành cho mạng 78 host và mạng 50 host. Do đó ta chỉ có thể lấy từ mạng 172.16.5.192/27 trở đi để gán cho mạng 20 host. Ở đây ta lấy mạng 172.16.5.192/27 gán cho mạng 20 host.

Tiếp đó ta xét đến mạng có 10 host, ta xem xem mượn bao nhiêu bit là phù hợp:

- 2^m – 2 ≥ 11
- m + n = 8 (mượn bit ở octet thứ 4). Với m: số bit host, n: số bit mượn

Ta được m = 4 và n = 4 Vậy ta mượn 4 bit, mạng 172.16.5.0/28 được chia thành 16 mạng 172.16.5.0/28, 172.16.5.16/28, 172.16.5.32/28,..., 172.16.5.226/28, 172.16.5.240/28. Tuy nhiên các dải địa chỉ của các mạng 172.16.5.0/28, ..., 172.16.5.224/28 đã được giành cho mạng 78 host và mạng 50 host, mạng 20 host. Do đó ta chỉ có thể lấy từ mạng 172.16.5.226/28 trở đi để gán cho mạng 10 host. Ở đây ta lấy mạng 172.16.5.226/28 gán cho mạng 10 host.

Tiếp đó ta xét đến mạng có 5 host, ta xem xem mượn bao nhiêu bit là phù hợp:

- 2^m – 2 ≥ 6
- m + n = 8 (mượn bit ở octet thứ 4). Với m: số bit host, n: số bit mượn

Ta được m = 3 và n = 5 Vậy ta mượn 5 bit, mạng 172.16.5.0/29 được chia thành 32 mạng 172.16.5.0/29, 172.16.5.8/29, 172.16.5.16/29, ..., 172.16.5.242/29, 172.16.5.248/29. Tuy nhiên các dải địa chỉ của các mạng 172.16.5.0/29, ..., 172.16.5.240/29 đã được giành cho mạng 78 host và mạng 50 host, mạng 20 host, mạng 10 host. Do đó ta chỉ có thể lấy từ mạng 172.16.5.242/29 trở đi để gán cho mạng 5 host. Ở đây ta lấy mạng 172.16.5.242/29 gán cho mạng 5 host.

Tiếp đó ta xét đến các mạng có 2 host là các liên kết điểm - điểm serial, ta xem thử mượn bao nhiêu bit là phù hợp:

- 2^m – 2 ≥ 2
- m + n = 8 (mượn bit ở octet thứ 4). Với m: số bit host, n: số bit mượn

Ta được m = 2 và n = 6 là tối ưu hơn cả, đảm bảo không bị dư địa chỉ. Vậy ta mượn 6 bit, mạng 172.16.5.0/24 được chia thành 2^6 = 64 mạng 172.16.5.0/30, 172.16.5.4/30, 172.16.5.8/30, ..., 172.16.5.248/30, 172.16.5.252/30. Tuy nhiên các dải địa chỉ của các mạng 172.16.5.0/30, ..., 172.16.5.247/30 đã được giành cho mạng 78 host, mạng 50 host và mạng 20 host, mạng 10 host, mạng 5 host . Do đó ta chỉ có thể lấy từ mạng 172.16.5.248/30 để gán cho các mạng 2 host. Ở đây ta lấy mạng 172.16.5.248/30 và 172.16.5.252/30 gán cho hai liên kết serial.

## 4.6.3. Cho các địa chỉ host sau đây. Hãy xác định các địa chỉ subnet tương ứng và cho biết địa chỉ này có thể dùng đặt cho host được không:

### a, 192.168.1.130/29

/29 => có 29 bit mạng. Octet bị chia cắt là octet thứ 4 => số bit mượn của octet này là 5 => bước nhảy là 8. Lấy octet thứ 4 của địa chỉ host là 130 chia cho 8 được 16 và còn dư. Ta lấy 16 nhân với 8 được 128. Host này thuộc mạng 192.168.1.128

192.168.1.130 nằm trong dải host (192.168.1.128 -> 192.168.1.135) => Có thể dùng đặt cho host.

### b, 172.16.34.57/18

/18 => có 18 bit mạng. Octet bị chia cắt là octet thứ 3 => số bit mượn của octet này là 2 => bước nhảy là 64. Lấy octet thứ 3 của địa chỉ host là 57 chia cho 64 được 0 và còn dư. Ta lấy 0 nhân với 64 được 0. Host này thuộc mạng 172.16.34.57

172.16.34.57/18 nằm trong dải host (172.16.0.0 - 172.16.63.255) => Có thể dùng đặt cho host.

### c, 203.162.4.191/28

/28 => có 28 bit mạng. Octet bị chia cắt là octet thứ 4 => số bit mượn của octet này là 4 => bước nhảy là 16. Lấy octet thứ 4 của địa chỉ host là 191 chia cho 16 được 11 và còn dư. Ta lấy 11 nhân với 16 được 176. Host này thuộc mạng 203.162.4.176

203.162.4.191/28 là địa chỉ broadcast của subnet (203.162.4.176 - 203.162.4.191) => Không thể dùng đặt cho host.

### d, 1.1.1.1/30

/30 => có 30 bit mạng. Octet bị chia cắt là octet thứ 4 => số bit mượn là 6 => bước nhảy là 4. Lấy octet thứ 4 của host là 1 chia 4 được 0 còn dư. Ta lấy 0 nhân 4 bằng 0. Host này thuộc mạng 1.1.1.0

1.1.1.1/30 là địa chỉ host đầu nằm trong dải host (1.1.1.0 - 1.1.1.3) => có thể dùng làm host

### e, 10.10.10.89/29

/29 => có 29 bit mạng. Octet bị chia cắt là octet thứ 4 => số bit mượn là 5 => bước nhảy là 8. Lấy octet thứ 4 của host là 89 chia 8 được 11 còn dư. Ta lấy 11 nhân 8 bằng 88. Host này thuộc mạng 10.10.10.88

10.10.10.89/29 là địa chỉ host đầu nằm trong dải host (10.10.10.88 - 10.10.10.95) => có thể dùng làm host

### f, 70.9.12.35/30

/30 => có 30 bit mạng. Octet bị chia cắt là octet thứ 4 => số bit mượn là 6 => bước nhảy là 4. Lấy octet thứ 4 của host là 35 chia 4 được 8 còn dư. Ta lấy 8 nhân 4 bằng 32. Host này thuộc mạng 70.9.12.32

70.9.12.35/30 là địa chỉ broadcast (70.9.12.32 - 70.9.12.35). => không làm địa chỉ host

### g, 158.16.23.208/29

/29 => có 29 bit mạng. Octet bị chia cắt là octet thứ 4 => số bit mượn là 5 => bước nhảy là 8. Lấy octet thứ 4 của host là 208 chia 8 được 26. Host này thuộc mạng 158.16.23.208 .32   
158.16.23.208 là địa chỉ mạng (158.16.23.208 - 158.16.23.215) => không dùng làm host

### 4.6.4. Hãy tóm tắt các địa chỉ mạng sau đây về thành một địa chỉ mạng đại diện:

a, 192.168.0.0/24
192.168.1.0/24
192.168.2.0/24
192.168.3.0/24

Octet thứ ba là octet khác nhau đầu tiên. Ta xét chi tiết octet này:Ta xét chi tiết octet này:

192.168.|000000|00.0

192.168.|000000|01.0

192.168.|000000|10.0

192.168.|000000|11.0

Ta thấy octet thứ ba còn có thêm 6 bit giống nhau. Vậy ta có mạng tóm tắt là 192.168.0.0/22. Chú ý: subnet mask bây giờ là 255.255.252.0 với prefix là 22.

b, 172.16.16.0/24
172.16.20.0.24
172.16.24.0/24
172.16.28.0/24

Octet thứ ba là octet khác nhau đầu tiên. Ta xét chi tiết octet này:Ta xét chi tiết octet này:

172.16.|0001|0000.0

172.16.|0001|0100.0

172.16.|0001|1000.0

172.16.|0001|1100.0

Ta thấy octet thứ ba còn có thêm 4 bit giống nhau. Octet 3: giữ 4 bit chung “0001” và các bit còn lại đặt về 0 -> 00010000 = 16 Vậy có mạng tóm tắt là → 172.16.16.0/20. Chú ý: subnet mask bây giờ là 255.255.240.0 với prefix là 20.