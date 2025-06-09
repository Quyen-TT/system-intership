# Tổng quan về TCPdump

## 1. Tcpdump là gì?

Tcpdump là công cụ hỗ trợ phân tích các gói dữ liệu mạng theo dòng lệnh, cho phép chặn và lọc các gói tin TCP/IP được truyền đi hoặc được nhận trên một mạng mà máy tính có tham gia. tcmpdump sẽ lưu lại những gói tin đã bắt được, sau đó dùng để phân tích.

Hiểu đơn giản, Tcpdump là công cụ dò mạng tìm Netwwork,  có vai trò trong việc gỡ rối và kiểm tra các vấn đề liên quan đến bảo mật và kết nối mạng.

## 2. Tcpdump tồn tại ở hình thức nào?

Để lựa chọn gói tin phù hợp với biểu thức logic mà người dùng nhập vào, tcmpdump sẽ xuất ra màn hình một gói tin chạy trên card mạng mà máy chủ đang lắng nghe.  

Tùy vào các lựa chọn khác nhau người dùng có thể xuất mô tả này ra một gói tin thành một file "pcap" để phân tích và có thể đọc nội dung "pcap" đó với option -r của lệnh tcpdump, hoặc sử dụng các phần mềm khác như là : Wireshark.

Đối với những trường hợp không có tùy chọn, lệnh tcpdump sẽ được chạy cho đến khi nhận được một tín hiệu ngắt từ người dùng. Sau khi kết thúc việc bắt các gói tin, tcmpdump sẽ báo cáo các cột sau:

- Packet capture: số lượng gói tin bắt được và xử lý.

- Packet received by filter: số lượng gói tin được nhận bởi bộ lọc.

- Packet dropped by kernel: số lượng packet đã bị dropped bởi cơ chế bắt gói tin của hệ điều hành.

## 3. Định dạng chung của một dòng giao thức Tcpdump

Định dạng chung của một dòng giao thức tcmpdump: 

    time-stamp src > dst:  flags  data-seqno  ack  window urgent options

- Time-stamp: hiển thị thời gian gói tin được capture.

- Src và dst: hiển thị địa IP của người gửi và người nhận.

- Cờ Flag thì bao gồm các giá trị sau:

    - S(SYN):  Được sử dụng trong quá trình bắt tay của giao thức TCP.

    - .(ACK):  Được sử dụng để thông báo cho bên gửi biết là gói tin đã nhận được dữ liệu thành công.

    - F(FIN): Được sử dụng để đóng kết nối TCP.

    - P(PUSH): Thường được đặt ở cuối để đánh dấu việc truyền dữ liệu.

    - R(RST): Được sử dụng khi muốn thiết lập lại đường truyền.

    - Data-sqeno: Số sequence number của gói dữ liệu hiện tại.

    - ACK: Mô tả số sequence number tiếp theo của gói tin do bên gởi truyền (số sequence number mong muốn nhận được).

    - Window: Vùng nhớ đệm có sẵn theo hướng khác trên kết nối này.

    - Urgent: Cho biết có dữ liệu khẩn cấp trong gói tin.

## 5. Cài đặt một số lệnh sử dụng Tcpdump cơ bản

Cài đặt Tcpdump:

- Ubuntu

    sudo apt-get install tcpdump -y

- CentOS

    sudo yum install tcpdump -y

Một số lệnh cơ bản của tcmpdump

![anh17](/QuyenNV/DHCP/images/anh17.png)

- Bắt gói tin theo địa chỉ nguồn 

    tcpdump -i <interfaces> src <src ip>

- Bắt gói tin theo địa chỉ đích

    tcpdump -i <interfaces> dst <dst ip>

- Xem các interface đang hoạt động

    tcpdump -D

![anh18](/QuyenNV/DHCP/images/anh18.png)

- Bắt gói tin trên interface

    tcpdump -i
- Bắt các gói theo port

    tcpdump -i enp0s3 port 22 -c 5 -n

![anh19](/QuyenNV/DHCP/images/anh19.png)

    -n: Hiển thị số port thay cho tên giao thức, IP thay cho Hostname

- Bắt theo các gói TCP giữa hai host

    tcpdump -i enp0s3 tcp -c 5

![anh20](/QuyenNV/DHCP/images/anh20.png)

- Lưu file .pcap (Wireshark)

    tcpdump -i enp0s3 capture.pcap

- Đọc file PCAP

    tcpdump -r capture.pcap