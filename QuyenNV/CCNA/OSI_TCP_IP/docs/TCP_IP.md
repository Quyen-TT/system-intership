# Tìm hiểu về mô hình TCP/IP

## 1. Giới thiệu về mô hình TCP/IP

TCP/IP (Transmission Control Protocol/Internet Protocol) là một bộ giao thức truyền thông xác định các tiêu chuẩn để truyền dữ liệu qua mạng máy tính, bao gồm cả internet. Giao thức TCP/IP là nền tảng của internet và cho phép các thiết bị giao tiếp với nhau bằng một ngôn ngữ chung.

TCP/IP gồm 2 giao thức chính

- TCP: Có chức năng xác định các ứng dụng và tạo ra các kênh giao tiếp. TCP cũng có chức năng quản lý các thông tin khi được chia nhỏ để truyền tải qua internet. Giao thức này sẽ tập hợp các thông tin này theo đúng thứ tự, đảm bảo truyền tải thông tin chính xác tới địa chỉ đến.

- IP: Đảm bảo thông tin được truyền đến đúng địa chỉ. IP sẽ gán các địa chỉ và định tuyến từng gói thông tin. Mỗi mạng sẽ có 1 địa chỉ IP để xác định được chính xác nơi chuyển/nhận thông tin, dữ liệu.

## 2. Cấu trúc mô hình TCP/IP

Mô hình TCP/IP tiêu chuẩn bao gồm 4 tầng:

- Tầng 1: Tầng truy cập mạng (Network Access)
- Tầng 2: Tầng mạng (Internet)
- Tầng 3: Tầng giao vận (Transport)
- Tầng 4: Tầng ứng dụng (Application)

![OSI10](/QuyenNV/CCNA/OSI_TCP_IP/images/osi10.png)

### 2.1 Tầng truy cập mạng (Network Access layer)

Tương ứng với hai tầng vật lý và liên kết dữ liệu trong mô hình OSI, tầng truy cập mạng trong mô hình TCP/IP đảm bảo việc gửi và nhận dữ liệu trên phương tiện vật lý của mạng. 

Tầng này xử lý tất cả vấn đề liên quan đến cách dữ liệu được truyền từ thiết bị này sang thiết bị khác. Bao gồm việc đóng gói dữ liệu thành khung (frame), xác định địa chỉ vật lý, và kiểm soát quyền truy cập vào môi trường truyền dẫn.

### 2.2 Tầng mạng (Internet layer)

Tầng mạng có trách nhiệm chính trong việc định tuyến các gói tin từ nguồn đến đích. Tầng này sử dụng giao thức IP để xác định địa chỉ duy nhất cho mỗi thiết bị và quyết định đường đi của dữ liệu trong mạng. Tầng mạng đảm nhận việc phân mảnh và tái tổ hợp các gói tin, xử lý lỗi, và cập nhật các thông tin định tuyến.

Các giao thức của lớp này bao gồm:

- IP – Internet Protocol
- ICMP – Internet Control Message Protocol
- IGMP- Internet Group Message Protocol

### 2.3 Tầng giao vận (Transport layer)

Tầng giao vận xử lý các vấn đề liên quan đến giao tiếp giữa các máy chủ. Dữ liệu ở tầng này được chia thành các đoạn, với kích thước không đều nhau.

Tầng này bao 2 gồm giao thức là: TCP (đảm bảo chất lượng dữ liệu) và UDP (truyền tải nhanh hơn nhưng không đảm bảo chất lượng).

![OSI11](/QuyenNV/CCNA/OSI_TCP_IP/images/osi11.png)

### 2.4 Tầng ứng dụng (Application Layer)

Tầng ứng dụng cung cấp các dịch vụ mạng cần thiết cho các ứng dụng mà người dùng sử dụng, như trình duyệt web, email, và các dịch vụ truyền file.

Tầng này cung cấp các giao thức ứng dụng như HTTP, SMTP, FTP, ..., đảm bảo người dùng có thể tương tác với mạng một cách suôn sẻ và hiệu quả.

## 3. So sánh mô hình OSI và TCP/IP

**Giống nhau:**

- Đều có kiến trúc phân lớp.
- Đều có lớp Network và lớp Transport.
- OSI và TCP/IP cùng sử dụng kỹ thuật chuyển Packet.

**Khác nhau:**

- Sự đơn giản

  - TCP/IP có 4 tầng, trong khi OSI có 7 tầng. Điều này làm cho TCP/IP trở nên đơn giản và dễ áp dụng hơn trong các ứng dụng thực tế.
  - OSI phân chia rõ ràng từng lớp chức năng, trong khi TCP/IP có thể kết hợp một số tầng của OSI vào một tầng (ví dụ: Tầng trình diễn và phiên của OSI đều được kết hợp trong Tầng Ứng Dụng của TCP/IP).

- Ứng dụng thực tế

  - TCP/IP đã được triển khai và sử dụng rộng rãi trong mọi mạng, bao gồm cả Internet, trong khi OSI chủ yếu là một mô hình lý thuyết để hiểu về các giao thức mạng.
  - Hầu hết các giao thức trong TCP/IP đều thực tế và được sử dụng cho các hệ thống mạng hiện đại, trong khi các giao thức của OSI không được triển khai nhiều trong các mạng thực tế.

- Tính linh hoạt

  - TCP/IP có tính linh hoạt cao và hỗ trợ nhiều giao thức khác nhau cho từng ứng dụng cụ thể (HTTP, FTP, SMTP...), trong khi OSI chủ yếu là một khung lý thuyết không quy định cụ thể giao thức.

## 4. Workflow với mô hình TCP/IP

Bước 1: Ở tầng Application, bên A tạo ra dữ liệu, sau đó dữ liệu sẽ được chuyển xuống các tầng thấp hơn. Ở mỗi tầng, một header (và đôi khi là trailer) sẽ được bổ sung để giúp dữ liệu được truyền đi đúng cách.

Bước 2: Tiếp theo, dữ liệu được chuyển xuống tầng Transport, tại đây dữ liệu có thể bị chia nhỏ thành các segment. Ở tầng này có 2 giao thức là TCP và UDP. gói tin sẽ sử dụng 1 trong 2 giao thức này: **Nếu là giao thức TCP:**

***Thiết lập kết nối: Bắt tay 3 bước***

![OSI13](/QuyenNV/CCNA/OSI_TCP_IP/images/osi13.png)

- Bước 1: Máy A khởi tạo kết nối bằng cách gửi một gói tin TCP SYN đến máy B. Gói SYN này chứa số thứ tự ban đầu (Initial Sequence Number - ISN) do máy A chọn (ví dụ: seq = 5432).

- Bước 2: Máy B nhận được gói SYN từ A và phản hồi bằng một gói SYN-ACK. Gói này chứa: số thứ tự của máy B, số xác nhận (ACK) của gói SYN từ A, tức là seq của A + 1.

- Bước 3: Máy A xác nhận phản hồi từ máy B bằng cách gửi một gói ACK. Gói này chứa: Số xác nhận ACK = seq của B + 1, xác nhận rằng A đã nhận gói SYN-ACK từ B thành công. Kết nối được thiết lập thành công.

***Truyền dữ liệu:***

Sau khi kết nối được thiết lập, các thiết bị có thể bắt đầu truyền tải dữ liệu. Dữ liệu được chia thành các phân đoạn nhỏ hơn và đánh số tuần tự. Máy A gửi các phân đoạn này đến người nhận qua kết nối đã thiết lập. Mỗi phân đoạn được đánh số thứ tự để cho phép Máy B xác định và lắp ráp chúng lại theo đúng thứ tự ban đầu.

***Đóng kết nối:***

![OSI15](/QuyenNV/CCNA/OSI_TCP_IP/images/osi15.png)

Khi quá trình truyền tải hoàn tất, hai thiết bị có thể đóng kết nối. 

- Bước 1: Máy A gửi một thông điệp FIN (Finish) để cho biết nó đã hoàn thành việc truyền tải dữ liệu. 

- Bước 2: Máy B sẽ gửi một ACK để xác nhận việc nhận thông điệp FIN và sẵn sàng đóng kết nối. 

- Bước 3: Sau đó, Máy B sẽ gửi một thông điệp FIN để yêu cầu đóng kết nối từ phía Máy A. 

- Bước 4: Máy A sẽ gửi một ACK xác nhận việc nhận thông điệp FIN từ Máy B. Kết nối được đóng.

![OSI14](/QuyenNV/CCNA/OSI_TCP_IP/images/osi14.png)

Bước 3: Dữ liệu tiếp tục được chuyển xuống tầng Network, tại đây mỗi Segment được đóng gói thành một Packet Header IP sẽ được thêm vào Packet, bao gồm địa chỉ IP nguồn và IP đích. Sau đó, thiết bị thực hiện tìm next-hop (router tiếp theo) để định tuyến gói tin đi đúng hướng.

Bước 4: Ở tầng network access, tầng này chính là tầng datalink và tầng physical ở mô hình osi.

Dữ liệu tiếp tục được chuyển xuống tầng Data Link. tại đây Packet sẽ được đóng gói thành Frame bằng cách thêm địa chỉ MAC nguồn (MAC của thiết bị hiện tại) và địa chỉ MAC đích (MAC của router tiếp theo). Đồng thời, Trailer (FCS - Frame Check Sequence) được thêm vào để kiểm tra lỗi trong quá trình truyền.

Cuối cùng, mỗi Frame sẽ được tầng Vật Lý chuyển thành một chuỗi bit nhị phân và được mã hóa thành tín hiệu điện, quang hoặc sóng vô tuyến để truyền đến thiết bị B qua môi trường mạng.




