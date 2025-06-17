# Tìm hiểu về mô hình OSI

## 1. Giới thiệu về mô hình OSI

Mô hình OSI (Open Systems Interconnection) là một tập hợp các quy tắc giải thích cách các hệ thống máy tính khác nhau giao tiếp qua mạng. Mô hình OSI bao gồm 7 tầng, mỗi tầng có các chức năng và trách nhiệm riêng biệt. Cách tiếp cận phân tầng này giúp các thiết bị và công nghệ khác nhau có thể hoạt động cùng nhau một cách dễ dàng. Mô hình OSI cung cấp một cấu trúc rõ ràng cho việc truyền dữ liệu và quản lý các vấn đề về mạng. Mô hình OSI được sử dụng rộng rãi như một tài liệu tham khảo để hiểu cách các hệ thống mạng hoạt động.

![OSI1](/QuyenNV/1.CCNA/OSI_TCP_IP/images/osi1.png)

## 2. Các tầng trong mô hình OSI

### 2.1 Tầng vật lý (Physical layer)

**Tầng vật lý** là tầng đầu tiên và thấp nhất trong mô hình OSI. Đây là tầng chịu trách nhiệm truyền tải dữ liệu dưới dạng tín hiệu vật lý (điện, quang hoặc vô tuyến) qua các môi trường truyền dẫn như cáp mạng, cáp quang, sóng radio, ... Tầng này không quan tâm đến nội dung của dữ liệu mà chỉ đảm bảo việc truyền tải các bit (0 và 1) từ thiết bị gửi đến thiết bị nhận một cách chính xác.

Thiết bị liên quan: Cáp mạng (Ethernet, cáp quang, cáp đồng trục, cáp xoắn đôi), Hub, Repeater, Modem.

![OSI2](/QuyenNV/1.CCNA/OSI_TCP_IP/images/osi2.png)

**Chức năng của tầng vật lý**

- Biểu diễn dữ liệu dưới dạng bit: dữ liệu tầng vật lý là luồng bit liên tục 0 và 1. Để truyền đi, các bit phải được mã hóa thành các tín hiệu điện, quang hoặc tần số vô tuyến.

- Tốc độ truyền dẫn: Qui định số lượng bit được gửi đi trong một đơn vị thời gian và khoảng thời gian để truyền đi một bit.

- Đồng bộ: Máy gửi và nhận phải được đồng bộ hóa ở mức bit.

- Hình trạng vật lý: Hình trạng vật lý xác định cách nối các thiết bị với nhau để tạo thành mạng. Có ba hình trạng cơ bản: dạng bus, dạng vòng và dạng sao.

- Chế độ truyền dẫn: Tầng vật lý cũng xác định hướng truyền dữ liệu giữa hai thiết bị: đơn công (simplex), bán song công (half-duplex) hay song công (full-duplex). Trong chế độ đơn công, một thiết bị chỉ có thể gửi hoặc nhận dữ liệu. Chế độ đơn công là truyền thông một chiều. Trong chế độ bán song công, một thiết bị có thể gửi và nhận dữ liệu, nhưng không phải tại cùng một thời điểm. Trong chế độ song công, một thiết bị có thể nhận và gửi dữ liệu tại cùng một thời điểm. 

### 2.2 Tầng liên kết dữ liệu (Data Link layer)

**Tầng liên kết dữ liệu** là tầng thứ hai trong mô hình OSI. Nó chịu trách nhiệm cho việc truyền dữ liệu an toàn qua các đường truyền vật lý và xác định địa chỉ vật lý (MAC address). Tầng Liên kết dữ liệu cung cấp các dịch vụ cho tầng mạng và có hai phân lớp con:

- Logical Link Control (LLC - Kiểm soát liên kết logic): quản lý các quy tắc truyền thông đồng bộ và không đồng bộ, kiểm soát lỗi và kiểm tra tính toàn vẹn của dữ liệu. Nó đảm bảo việc truyền thông tin một cách tin cậy giữa các điểm cuối trên cùng một mạng liên kết.

- Media Access Control (MAC - Kiểm soát truy cập phương tiện): Lớp MAC xác định cách truy cập vào phương tiện truyền thông chia sẻ, chẳng hạn như mạng LAN Ethernet. Nó quản lý việc gán địa chỉ vật lý (MAC address) cho các thiết bị mạng và xử lý việc truyền dữ liệu giữa các đầu cuối trên cùng một mạng.

Thiết bị liên quan: Switch, Bridge, Network Interface Card (NIC - Card mạng).

![OSI3](/QuyenNV/1.CCNA/OSI_TCP_IP/images/osi3.png)

**Chức năng của tầng liên kết dữ liệu**

- Tạo khung dữ liệu: Tầng liên kết dữ liệu chia gói tin nhận được từ tầng mạng thành các đơn vị dữ liệu gọi là các khung dữ liệu.

- Định địa chỉ vật lý (Physical Addressing): Sau khi tạo khung, tầng liên kết dữ liệu thêm địa chỉ vật lý (địa chỉ MAC) của người gửi và/hoặc người nhận vào phần tiêu đề (Header) của mỗi khung để đảm bảo dữ liệu được chuyển đúng thiết bị đích.

- Kiểm soát lưu lượng: Nếu tốc độ nhận dữ liệu nhỏ hơn tốc độ gửi dữ liệu, tầng liên kết dữ liệu phải thực hiện một kỹ thuật kiểm soát lưu lượng để ngăn ngừa tình trạng quá tải tại nơi nhận.

- Kiểm soát lỗi: Tầng liên kết dữ liệu làm tăng tính tin cậy cho tầng vật lý bằng cách sử dụng một kỹ thuật phát hiện và truyền lại các khung bị lỗi hoặc bị mất. Nó cũng sử dụng kỹ thuật ngăn ngừa hiện tượng lặp khung. Kiểm soát lỗi thường được thực hiện bằng cách thêm một thông tin điều khiển vào phần cuối của khung, thông thường người ta sử dụng kỹ thuật kiểm tra vòng (CRC – Cyclic Redandunce Check).

- Kiểm soát truy cập: Khi nhiều thiết bị được nối với cùng một đường truyền, tầng con MAC (Media Access Control) của tầng liên kết dữ liệu sẽ quyết định thiết bị nào có quyền kiểm soát kênh truyền tại một thời điểm nhất định.

### 2.3 Tầng mạng (Network Layer)

**Tầng mạng** là tầng thứ ba trong mô hình OSI. Tầng này có trách nhiệm quản lý việc định tuyến và chuyển tiếp dữ liệu giữa các mạng khác nhau trong hệ thống mạng.

Các giao thức phổ biến: IP (Internet Protocol), ICMP (Internet Control Message Protocol), và ARP (Address Resolution Protocol).

![OSI4](/QuyenNV/1.CCNA/OSI_TCP_IP/images/osi4.png)

**Chức năng của tầng mạng**

- Định tuyến (Routing): Quyết định đường đi tối ưu cho các gói dữ liệu từ nguồn đến đích.

- Địa chỉ hóa (Addressing): Sử dụng địa chỉ logic (ví dụ: IP) để định danh các thiết bị trong mạng.

- Chuyển mạch (Switching): Chuyển các gói dữ liệu giữa các thiết bị mạng.

- Kiểm soát tắc nghẽn (Congestion Control): Quản lý lưu lượng mạng để tránh tắc nghẽn.

- Phân mảnh và hợp nhất (Fragmentation and Reassembly): Phân mảnh các gói dữ liệu lớn thành các gói nhỏ hơn để truyền qua mạng và hợp nhất chúng tại đích.

### 2.4 Tầng giao vận (Transport Layer)

**Tầng giao vận** là tầng thứ tư trong mô hình OSI. Đây là tầng chịu trách nhiệm đảm bảo dữ liệu được truyền tải một cách đáng tin cậy, đúng thứ tự và không bị mất mát giữa hai thiết bị trong mạng.

Các giao thức phổ biến:

- TCP (Transmission Control Protocol): Đảm bảo dữ liệu đến đúng thứ tự và không bị mất (kết nối đáng tin cậy).

- UDP (User Datagram Protocol): Gửi dữ liệu nhanh nhưng không đảm bảo đầy đủ (kết nối không đáng tin cậy).

![OSI5](/QuyenNV/1.CCNA/OSI_TCP_IP/images/osi5.png)

**Chức năng của tầng giao vận**

- Chia nhỏ và tái tạo dữ liệu (Segmentation & Reassembly): Khi dữ liệu từ tầng ứng dụng quá lớn để gửi đi một lần, tầng giao vận chia dữ liệu thành nhiều segment nhỏ hơn. Khi đến đích, các segment này được lắp ghép lại theo đúng thứ tự để tái tạo dữ liệu ban đầu. TCP đánh số từng segment để đảm bảo chúng được ghép nối đúng.

- Đa kết nối (Connection Multiplexing): Tầng Giao vận hỗ trợ việc thiết lập và duy trì các kết nối mạng đa kết nối (multi-connection), cho phép nhiều ứng dụng trên cùng một thiết bị mạng gửi và nhận dữ liệu đồng thời.

- Điều khiển luồng (Flow Control): Tầng Giao vận quản lý việc truyền dữ liệu giữa các ứng dụng và điều chỉnh tốc độ truyền để đảm bảo rằng không bị quá tải hoặc quá chậm so với nguồn tiêu thụ.

- Kiểm soát lỗi (Error Control): Tầng Giao vận sử dụng các cơ chế kiểm soát lỗi như checksum và ACK/NACK để đảm bảo rằng dữ liệu được truyền một cách tin cậy và không bị lỗi.

### 2.5 Tầng phiên (Session Layer) 

**Tầng phiên** là tầng thứ năm trong mô hình OSI. Đây là tầng có nhiệm vụ thiết lập, duy trì và kết thúc phiên giao tiếp giữa hai thiết bị trong mạng.

Các giao thức phổ biến: NetBIOS, RPC (Remote Procedure Call), PPTP (Point-to-Point Tunneling Protocol).

![OSI6](/QuyenNV/1.CCNA/OSI_TCP_IP/images/osi6.png)

**Chức năng của tầng phiên**

- Thiết lập, Duy trì và Kết thúc Phiên (Session Establishment, Maintenance, and Termination): Tầng phiên cho phép hai tiến trình thiết lập, sử dụng và kết thúc một kết nối.

- Đồng bộ hóa (Synchronization): Tầng phiên cho phép một tiến trình thêm các điểm kiểm tra (checkpoint) được coi là các điểm đồng bộ trong dữ liệu. Những điểm đồng bộ này giúp xác định lỗi để dữ liệu có thể được đồng bộ hóa lại một cách chính xác, tránh việc cắt ngang tin nhắn một cách đột ngột và ngăn ngừa mất dữ liệu.

- Kiểm soát hội thoại (Dialog Controller): Tầng phiên cho phép hai hệ thống bắt đầu giao tiếp với nhau theo chế độ bán song công (Half-Duplex) hoặc song công toàn phần (Full-Duplex).

### 2.6 Tầng trình diễn (Presentation layer)

**Tầng trình diễn** là tầng thứ sáu trong mô hình OSI. Tầng này chịu trách nhiệm chuyển đổi, mã hóa, giải mã và nén dữ liệu, đảm bảo dữ liệu từ hệ thống gửi có thể được hiểu đúng bởi hệ thống nhận.

Các giao thức phổ biến:

- SSL/TLS (Bảo mật dữ liệu - HTTPS).
- JPEG, PNG (Định dạng ảnh).
- MP3, MP4 (Định dạng âm thanh, video).

![OSI7](/QuyenNV/1.CCNA/OSI_TCP_IP/images/osi7.png)

**Chức năng của tầng phiên**

- Chuyển đổi định dạng (Translation): Ví dụ, chuyển đổi từ ASCII sang EBCDIC.

- Mã hóa/Giải mã (Encryption/Decryption): Mã hóa dữ liệu chuyển đổi dữ liệu sang một dạng khác hoặc mã hóa thành một chuỗi ký tự đặc biệt. Dữ liệu sau khi mã hóa được gọi là bản mã (ciphertext), còn dữ liệu sau khi giải mã trở lại trạng thái ban đầu được gọi là bản rõ (plain text).
Một khóa (key value) được sử dụng để thực hiện quá trình mã hóa và giải mã dữ liệu. 

- Nén dữ liệu (Compression): Giảm số lượng bit cần phải truyền qua mạng, giúp tối ưu băng thông và tăng tốc độ truyền dữ liệu.

### 2.7 Tầng ứng dụng (Application layer)

**Tầng ứng dụng** là tầng thứ bảy trong mô hình OSI. Đây là tầng gần nhất với người dùng, cung cấp giao diện để các ứng dụng có thể sử dụng mạng và giao tiếp với nhau.

Các giao thức phổ biến:

- HTTP/HTTPS (Web).
- FTP (Truyền file).
- SMTP, POP3, IMAP (Email).
- DNS (Chuyển đổi tên miền thành địa chỉ IP).

![OSI8](/QuyenNV/1.CCNA/OSI_TCP_IP/images/osi8.png)

**Chức năng của tầng phiên**

- Mạng thiết bị đầu cuối ảo (Network Virtual Terminal - NVT): Cho phép một người dùng đăng nhập vào một máy chủ từ xa.

- Truy cập và quản lý truyền tải tệp (File Transfer Access and Management - FTAM): Cho phép người dùng truy cập, tải xuống và quản lý các tệp từ một máy chủ từ xa.

- Dịch vụ thư điện tử (Mail Services): Cung cấp dịch vụ email để gửi và nhận thư điện tử.

- Dịch vụ danh bạ (Directory Services): Cung cấp nguồn dữ liệu phân tán và quyền truy cập vào thông tin toàn cầu về các đối tượng và dịch vụ trong mạng.

## 3. Workflow với mô hình OSI

![OSI9](/QuyenNV/1.CCNA/OSI_TCP_IP/images/osi9.png)

![OSI12](/QuyenNV/1.CCNA/OSI_TCP_IP/images/osi12.png)

Khi A gửi một dữ liệu đến B thì dữ liệu sẽ trải qua 2 tiến trình cơ bản là:

## Phía máy gửi: Quá trình đóng gói (Data Encapsulation)

Bước 1: Ở tầng Application, bên A tạo ra dữ liệu, sau đó dữ liệu sẽ được chuyển xuống các tầng thấp hơn. Ở mỗi tầng, một header (và đôi khi là trailer) sẽ được bổ sung để giúp dữ liệu được truyền đi đúng cách.

Bước 2: Tiếp theo, dữ liệu được chuyển xuống tầng Presentation để chuyển đổi sang định dạng chung, thực hiện mã hóa (nếu cần) và nén dữ liệu để tối ưu hóa băng thông. 

Bước 3: Sau đó, dữ liệu tiếp tục được gửi xuống tầng Session, nơi nó được bổ sung thông tin về phiên giao dịch, giúp duy trì kết nối giữa hai thiết bị.

Bước 4: Dữ liệu tiếp tục được chuyển xuống tầng Transport, tại đây dữ liệu có thể bị chia nhỏ thành nhiều Segment (nếu vượt quá kích thước tối đa). Mỗi Segment được gán thêm số port nguồn, số port đích, số thứ tự và mã kiểm tra lỗi để đảm bảo dữ liệu đến đúng ứng dụng và theo đúng thứ tự.

Bước 5: Dữ liệu tiếp tục được chuyển xuống tầng Network, tại đây mỗi Segment được đóng gói thành một Packet. Header IP sẽ được thêm vào Packet, bao gồm địa chỉ IP nguồn và IP đích. Sau đó, thiết bị thực hiện tìm next-hop (router tiếp theo) để định tuyến gói tin đi đúng hướng.

Bước 6: Tiếp đó, dữ liệu được chuyển xuống tầng Data Link, tại đây Packet sẽ được đóng gói thành Frame bằng cách thêm địa chỉ MAC nguồn (MAC của thiết bị hiện tại) và địa chỉ MAC đích (MAC của router tiếp theo). Đồng thời, Trailer (FCS - Frame Check Sequence) được thêm vào để kiểm tra lỗi trong quá trình truyền.

Bước 7: Cuối cùng, mỗi Frame sẽ được tầng Vật Lý chuyển thành một chuỗi bit nhị phân và được mã hóa thành tín hiệu điện, quang hoặc sóng vô tuyến để truyền đến thiết bị B qua môi trường mạng.

## Phía máy nhận: Quá trình mở gói dữ liệu (Data De-encapsulation)

Bước 1: Lớp Physical nhận tín hiệu từ môi trường truyền (tín hiệu điện, sóng vô tuyến, tín hiệu quang) và chuyển đổi thành chuỗi bit. Sau đó, các bit này được đặt vào bộ đệm và lớp Data Link được thông báo về việc dữ liệu đã được nhận.

Bước 2: Lớp Data Link kiểm tra lỗi trong Frame bằng FCS (Frame Check Sequence). Nếu phát hiện lỗi, Frame bị loại bỏ. Nếu Frame hợp lệ, địa chỉ MAC đích trong MAC Header được kiểm tra. Nếu địa chỉ này trùng với địa chỉ của thiết bị nhận, dữ liệu sau khi loại bỏ MAC Header và Trailer sẽ được chuyển lên lớp Network.

Bước 3: Lớp Network kiểm tra địa chỉ IP đích trong IP Header để xác định xem thiết bị nhận có phải là đích cuối cùng của gói tin không. Nếu đúng, IP Header sẽ bị loại bỏ và dữ liệu được chuyển lên lớp Transport để xử lý tiếp. Nếu thiết bị này không phải là đích cuối cùng, gói tin sẽ được định tuyến tiếp tục đến hop tiếp theo.

Bước 4: Lớp Transport xử lý dữ liệu dựa trên giao thức TCP hoặc UDP. Nếu sử dụng TCP, nó kiểm tra số thứ tự Sequence Number, thực hiện kiểm soát lỗi, xử lý gói tin phản hồi ACK/NAK để đảm bảo tất cả các segment đã đến đúng thứ tự. Sau khi tái tạo dữ liệu gốc, nó được chuyển lên lớp Session.

Bước 5: Lớp Session đảm bảo rằng các phiên giao tiếp vẫn được duy trì và dữ liệu đã được nhận đầy đủ. Sau khi hoàn tất quá trình xử lý phiên, dữ liệu (không còn Session Header) được chuyển lên lớp Presentation.

Bước 6: Lớp Presentation thực hiện giải mã (TLS/SSL), giải nén (ZIP, JPEG, MP3), hoặc chuyển đổi dữ liệu về định dạng phù hợp. Sau khi xử lý xong, dữ liệu được gửi lên lớp Application.

Bước 7: Lớp Application nhận dữ liệu đã được xử lý hoàn chỉnh. Sau đó, dữ liệu gốc được hiển thị trên ứng dụng của người dùng, hoàn thành quá trình truyền dữ liệu.