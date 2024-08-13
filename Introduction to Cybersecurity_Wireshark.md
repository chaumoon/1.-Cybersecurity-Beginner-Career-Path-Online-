I. Lý thuyết<br>
1. Wireshark<br>
- Wireshark là công cụ phân tích giao thức mạng phổ biến và hàng đầu thế giới
- cho phép bn xem những j xảy ra trên mạng of mk ở cấp độ vi mô và là tiêu chuẩn thực tế (thg là về mặt pháp lý)
đối vs doanh nghiệp thg mại và phi lợi nhuận, cơ quan chính phủ và tổ chức giáo dục
- nó liệt kê all các post trong máy và bắt đầu ghi lại all packet đc chuyển đến/từ máy bn
- sau đó can lưu packet thành file pcap và phân tích or phát hiện hành vi độc hại<br>

2. bắt đầu capture<br>
- chọn giao diện để capture lưu lg truy cập của nó sau đó nhấn vào nút blue trên thanh điều khiển
- khi bắt đầu capture packet, chg trình sẽ chuyển hg bn sang giao diện ms. nó có 3 phần:<br>
*. P1: <br>
- chứa all packet đc chuyển kể từ khi bn capture packet, liệt kê in4 quan trọng cho mỗi gói
- đánh số các gói và đặt các số này vào lift side
- liệt kê time tính bằng giây khi gói đc capture, điểm 0 là thời gian bn bắt đầu capture
- chứa IP nguồn và đích của packet, chứa giao thức đc xài trong gói, chứa ROW load/message của packet<br>
*. P2:<br>
- show data packet cho từng lớp mạng (OSI), bắt đầu từ top đến bottom từ lớp vật lý đến app
- kp all packet đều gửi đến lớp vật lí nên kp lúc nào cx thấy đủ 7 lớp ở phần này<br>
*. P3:<br>
- chứa all packet dạng hex, ngoài ra còn có bộ đếm các gói đã bắt đc<br>

*.Save the pcap: nhấn nút màu đỏ trên thanh điều khiển và ctrl s<br>

*. bắt đầu phân tích:<br>
- phân tích chung:<br>
+ 
