# Tìm hiểu về Routing, Static routing

## 1. Routing

### 1.1 Thế nào là routing

Định tuyến là phương thức mà Router (Bộ định tuyến) hay PC (thiết bị mạng) dùng để chuyển các gói tin đến địa chỉ đích một cách tối ưu nhất, nghĩa là chỉ ra hướng và đường đi tốt nhất cho gói tin. 

Router thu thập và duy trì các thông tin định tuyến để cho phép truyền và nhận các dữ liệu. Quá trình Routing dựa vào thông tin trên bảng định tuyến (Routing table), là bảng chứa các lộ trình nhanh và tốt nhất đến các mạng khác nhau trên mạng, để hướng các gói dữ liệu đi một cách hiệu quả nhất.

![anh1](/QuyenNV/CCNA/Routing/images/anh1.png)

Routing table là một dạng database cần thiết để tìm đường đi nhanh nhất (Path determination), nó thể được xây dựng thông qua nhiều cách, có thể là do cấu hình của người quản trị và cũng có thể được tích hợp trong các giao thức định tuyến.

![anh2](/QuyenNV/CCNA/Routing/images/anh2.png)

### 1.2 Các loại định tuyến

Routing được chia làm 2 phương thức chính là định tuyến tĩnh và định tuyến động.

![anh3](/QuyenNV/CCNA/Routing/images/anh3.png)

#### 1.2.1 Định tuyến tĩnh 

Định tuyến tĩnh là quá trình router thực hiện chuyển gói dữ liệu tới địa chỉ mạng đích dựa vào địa chỉ IP đích của gói dữ liệu. Để chuyển được gói dữ liệu đến đúng đích thì router phải học thông tin về đường đi tới các mạng khác. Thông tin về đường đi tới các mạng khác sẽ được người quản trị cấu hình cho router. Khi cấu trúc mạng thay đổi, người quản trị mạng phải tự thay đổi bảng định tuyến của router.

Kỹ thuật định tuyến tĩnh đơn giản, dễ thực hiện, ít hao tốn tài nguyên mạng và CPU xử lý trên router (do không phải trao đổi thông tin định tuyến và không phải tính toán định tuyến). Tuy nhiên kỹ thuật này không hội tụ với các thay đổi diễn ra trên mạng và không thích hợp với những mạng có quy mô lớn (khi đó số lượng route quá lớn, không thể khai báo bằng tay được).

- Ưu điểm:

    - Sử dụng ít bandwidth hơn định tuyến động.

    - Không tiêu tốn tài nguyên để tính toán và phân tích gói tin định tuyến.

- Nhược điểm:

    - Không có khả năng tự động cập nhật đường đi.

    - Phải cấu hình thủ công khi mạng có sự thay đổi.

    - Phù hợp với mạng nhỏ, rất khó triển khai trên mạng lớn

#### 1.2.2 Định tuyến động 

Các router sẽ trao đổi thông tin định tuyến với nhau. Từ thông tin nhận được, mỗi router sẽ thực hiện tính toán định tuyến từ đó xây dựng bảng định tuyến gồm các đường đi tối ưu nhất đến mọi điểm trong hệ thống mạng. Với định tuyến động, các router phải chạy các giao thức định tuyến (routing protocol). 

Giao thức định tuyến động không chỉ thực hiện chức năng tự tìm đường và cập nhật bảng định tuyến, nó còn có thể xác định tuyến đường đi tốt nhất thay thế khi tuyến đường đi tốt nhất không thể sử dụng được. Khả năng thích ứng nhanh với sự thay đổi mạng là lợi thế rõ rệt nhất của giao thức định tuyến động so với giao thức định tuyến tĩnh.

- Ưu điểm:

    - Đơn giản trong việc cấu hình.

    - Tự động tìm ra những tuyến đường thay thế khi mạng thay đổi.

- Nhược điểm:

    - Yêu cầu xử lí của CPU của router cao hơn so với định tuyến tĩnh.

    - Tiêu tốn một phần băng thông trên mạng để xây dựng bảng định tuyến.

## 2. Các giao thức định tuyến động 

Giao thức định tuyến động được chia thành hai nhóm chính:

- IGP (Interior Gateway Protocol - Giao thức định tuyến trong mạng nội bộ): Dùng trong cùng một hệ thống tự trị (Autonomous System), thường được sử dụng trong các mạng doanh nghiệp, trung tâm dữ liệu và ISP nội bộ.

- EGP (Exterior Gateway Protocol - Giao thức định tuyến liên mạng): Dùng để trao đổi thông tin giữa các hệ thống tự trị khác nhau (AS khác nhau), chủ yếu trên Internet.

![anh12](/QuyenNV/CCNA/Routing/images/anh12.png)

### 2.1 RIP (Routing Information Protocol)

**a, RIP là gì?** 

Routing Information Protocol (RIP) là giao thức định tuyến vector khoảng cách. Mỗi router sẽ gửi toàn bộ bảng định tuyến của nó cho router láng giềng theo định kỳ 30s/lần. Thông tin này lại tiếp tục được láng giềng lan truyền tiếp cho các láng giềng khác và cứ thế lan truyền ra mọi router trên toàn mạng. 

RIP chỉ sử dụng metric là hop-count để tính ra tuyến đường tốt nhất tới mạng đích. Vì sử dụng tiêu chí định tuyến là hop-count và bị giới hạn ở số hop là 15 nên giao thức này chỉ được sử dụng trong các mạng nhỏ dưới 15 hop (15 router). RIP có 2 phiên bản là RIP version 1 (RIPv1) và RIP version 2 (RIPv2).

**b, Cơ chế hoạt động**

RIP sử dụng thuật toán vector khoảng cách để quyết định đường đi nào để đưa một gói tin đến điểm đích của nó. Mỗi bộ định tuyến RIP duy trì một bảng định tuyến, đó là một danh sách các điểm đến mà bộ định tuyến biết cách đến. Mỗi bộ định tuyến gửi toàn bộ bảng định tuyến của mình tới các bộ định tuyến láng giềng gần nhất mỗi 30 giây. 

Trong ngữ cảnh này, láng giềng là các bộ định tuyến khác mà bộ định tuyến được kết nối trực tiếp - tức là các bộ định tuyến khác trên các đoạn mạng cùng với bộ định tuyến được chọn. Các bộ định tuyến láng giềng lại chuyển thông tin cho láng giềng gần nhất của chúng, và tiếp tục như vậy cho đến khi tất cả các máy chủ RIP trong mạng có cùng thông tin về các đường đi định tuyến. Sự chia sẻ thông tin này được gọi là sự hội tụ.

Nếu một bộ định tuyến nhận được cập nhật về một đường đi, và đường đi mới ngắn hơn, nó sẽ cập nhật mục bảng của mình với độ dài và địa chỉ next-hop của đường đi ngắn hơn. Nếu đường đi mới dài hơn, nó sẽ đợi qua một khoảng thời gian "hold-down" để xem liệu các cập nhật sau này có phản ánh giá trị cao hơn hay không. Nó chỉ cập nhật mục bảng nếu xác định rằng đường đi mới, dài hơn đã ổn định.

Nếu một bộ định tuyến gặp sự cố hoặc kết nối mạng bị ngắt, mạng phát hiện điều này vì bộ định tuyến đó ngừng gửi cập nhật cho các bộ định tuyến láng giềng của nó, hoặc ngừng gửi và nhận cập nhật qua kết nối bị ngắt. Nếu một tuyến đã cho trong bảng định tuyến không được cập nhật trong sáu chu kỳ cập nhật liên tiếp (tức là trong 180 giây), một bộ định tuyến RIP sẽ loại bỏ tuyến đó và thông báo vấn đề cho mạng thông qua các cập nhật định kỳ của riêng nó.

![anh4](/QuyenNV/CCNA/Routing/images/anh4.png)

### 2.2 OSPF (Open Shortest Path First)

**a, OSPF là gì?** 

OSPF là giao thức định tuyến nội hoạt động dựa vào thuật toán link state routing. Theo đó, mỗi bộ định tuyến sẽ chứa các thông tin của tất cả tên miền. Dựa vào những thông tin này, OSPF sẽ xác định quãng đường ngắn nhất. Điều này có nghĩa, mục tiêu chính của định tuyến là tìm hiểu về tuyến đường.

**b, Cơ chế hoạt động**

![anh5](/QuyenNV/CCNA/Routing/images/anh5.png)

**Bước 1:** Chọn Router-ID

Giao thức OSPF muốn hoạt động thì phải tạo ra một định danh gọi là Router-ID, với định dạng tương tự như địa chỉ IP.

![anh6](/QuyenNV/CCNA/Routing/images/anh6.png)

**Bước 2:** Thiết lập quan hệ láng giềng (neighbor) 

Router chạy giao thức định tuyến OSPF thực hiện gửi gói tin HELLO đến các cổng chạy OSPF trên cùng phân đoạn mạng, với tần suất mặc định 10s/lần. Mục đích của quá trình này là để Router tìm kiếm láng giềng, sau đó thiết lập và duy trì mối quan hệ.

![anh7](/QuyenNV/CCNA/Routing/images/anh7.png)

**Bước 3:** Trao đổi LSDB

LSDB đóng vai trò như tấm bản đồ mạng để Router có căn cứ tính toán định tuyến. Vì thế, LSDB sẽ giống nhau đối với các Router cùng vùng. Mỗi Router tiến hành trao đổi, giao tiếp với nhau theo từng đơn vị thông tin, được gọi là LSA. Tất cả LSA này được chứa trong những gói tin LSU (Link State Update) cụ thể mà các Router đã trao đổi thực tế.

![anh8](/QuyenNV/CCNA/Routing/images/anh8.png)

**Bước 4:** Tính toán đường đi ngắn nhất

Sau khi có LSDB hoàn chỉnh, router sử dụng thuật toán Dijkstra (Shortest Path First - SPF) để tính toán đường đi ngắn nhất đến từng mạng.

Trong OSPF không còn gọi là Metrict, thay vào đó gọi là Cost (Cost trên interface).

Cost được tính khi đi vào 1 cổng và đi ra không tính.

`Metric = cost = 10^8/Bandwidth (đơn vị bps)`

![anh9](/QuyenNV/CCNA/Routing/images/anh9.png)

### 2.3 BGP (Border Gateway Protocol)

**a, BGP là gì?**

BGP (Border Gateway Protocol) là giao thức định tuyến sử dụng để trao đổi thông tin định tuyến giữa các Hệ thống tự trị.

![anh10](/QuyenNV/CCNA/Routing/images/anh10.png)

**b, Các loại BGP** 

Các thiết bị hoặc mạng lân cận trong cùng một AS có thể sử dụng Internal BGP để định tuyến qua các mạng nội bộ. iBGP không giao tiếp với các AS khác vì quy trình chỉ xảy ra giữa hai đối tác peering nội bộ. 

External BGP là phần mở rộng của BGP. eBGP được sử dụng để truyền thông tin trao đổi giữa các hệ thống tự trị riêng biệt. Sử dụng eBGP KHÔNG yêu cầu cần sử dụng iBGP.

**c, Cơ chế hoạt động**

![anh11](/QuyenNV/CCNA/Routing/images/anh11.png) 

**Bước 1:** Thiết lập kết nối Neighbor (Peer)

- Hai router chạy BGP được gọi là BGP peers.

- BGP peers kết nối với nhau thông qua các kết nối TCP (Transmission Control Protocol).

- Khi kết nối được thiết lập, BGP peers trao đổi thông điệp cấu hình và các bản tin định tuyến.

**Bước 2:** Trao đổi thông tin định tuyến

- BGP peers trao đổi thông tin về các mạng IP mà chúng có thể định tuyến.

- Mỗi peer thông báo về các mạng mà nó biết đến và đường dẫn để đến các mạng đó.

- Thông điệp này chứa các thuộc tính của đường dẫn như AS_PATH (đường dẫn qua các Autonomous System), NEXT_HOP (địa chỉ IP của next-hop router), và các thuộc tính khác.

**Bước 3:** Chọn đường đi tốt nhất

- Giao thức này sử dụng thuật toán quyết định để lựa chọn đường dẫn tốt nhất.

- Các yếu tố quyết định bao gồm độ dài của AS_PATH, các thuộc tính được ưu tiên, độ ưu tiên của địa chỉ next-hop, và các tiêu chí khác.

- Đường dẫn được chọn sẽ được lưu vào bảng định tuyến BGP.

**Bước 4:** Cập nhật bảng định tuyến 

- Sau khi đường dẫn tốt nhất được xác định, nó sẽ được đưa vào bảng định tuyến của router.

- Router sử dụng thông tin trong bảng định tuyến để xác định cách chuyển tiếp gói tin giữa các mạng.

**Bước 5:** Duy trì và cập nhật

- BGP peers thường xuyên trao đổi các thông điệp keepalive để duy trì kết nối.

- Thông điệp update được sử dụng để thông báo về sự thay đổi trong mạng, ví dụ như khi có một đường dẫn mới hoặc một đường dẫn cũ không còn khả dụng.
