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

f, 10.0.0.0/8 mượn 5 bit.

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

g, 10.0.0.0/8 mượn 10 bit.

- số bit mượn là 10, số bit mạng bây giờ là 10 + 8 = 18
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

h, 10.0.0.0/8 mượn 18 bit.


