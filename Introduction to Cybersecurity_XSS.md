I. Lý thuyết<br>
1. XSS là gì<br>
- Cross-Site Scripting: là vul web dựa vào phía client mục đích là tiêm HTML or chạy code javascript trong browser của user
- hầu hết attack XSS đều để đánh cắp session cookie của user
- một số loại<br>
+ Reflected XSS: xảy ra khi user gửi data độc hại đến web app và data input của họ được phản ánh ngay lập tức trên web nơi browser xử lý data đó và kích hoạt attack
+ Stored XSS: tương tự Reflected XSS nhưng input độc hại đc lưu trữ trong web app và can đc gọi lại (VD: code độc hại trong cmt of web app đc lưu trong database và đc gọi bất cứ khi nào user xem cmt
+ DOM-based: đưa payload độc hại vào DOM, payload tồn tại trong môi trường phía client và nó sẽ ko tiếp cận đc backend code<br>

2. cách để test<br>
- khi check web app, phải kiểm tra all vector input nơi user can nhập data của họ
- trong khi check black box, phải đoán điều j đang diễn ra ở hậu trường và khai thác các chức năng phụ trợ để kích hoạt XSS attack
- khi check gray box, phải cung cấp đủ in4 về web app mà bn đang xử lý và các tính năng code của nó
- khi check white box bn đc cung cấp mã nguồn nên phải check mọi biến nhận đc từ user và theo dõi nó cho tới khi tìm thấy nơi nó phản ánh cụ thể
- việc check vector input can tự động bằng list payload đc xác định trước or theo cách thủ công
- input vector can là: HTML forms, GET/POST parameters, and Cookies.
- phải test cả kí tự đặc biệt của payload mà web app can lọc để tìm ra payload phù hợp cho input vector dễ vul<br>

3. Impact<br>
- can dùng tấn công XSS để đạt đc nh mục tiêu:<br>
+ ăn cắp cookie của user/chiếm quyền điều khiển session
+ kiểm soát web browser
+ thực hiện keylogging<br>

4. Phòng tránh<br>
- ko đc tin bất kì data đầu vào nào của user
- phải lọc và loại bỏ all kí tự đặc biệt can dẫn đến kiểu tấn công này
- PHP có 2 hàm để thoát data đầu vào:<br>
+ htmlspecialchars(): thay đổi các kí tự đặc biệt sau: ',",&,<,> to ', ", &, <, and >
+ htmlentities(): tương tự htmlspecialchars() nhưng nó sẽ mã hóa all kí tự có giá trị tg đương thực thể HTML<br>
- can xài filter_var() để lọc data đầu vào bằng bộ lọc đc chỉ định
- -> check mã nguồn thì kí tự đặc biệt đã bị thay đổi và payload ko thể hoạt động<br>

5. tool<br>
- https://portswigger.net/burp/communitydownload
- http://xss-proxy.sourceforge.net/<br>

II. lap: Searching for the cookie<br>
1. phát hiện 1 hộp tìm kiếm<br>

![image](https://github.com/user-attachments/assets/bd3e605c-75a2-4086-bbb1-4ac2bb7b44dd)<br>

2. tiêm thử 1 payload XSS đơn giản: <script>alert("xss")</script><br>

![image](https://github.com/user-attachments/assets/10c6a7d2-1325-47c4-b664-19f220639ca6)<br>

- đoạn script ko đc mã hóa -> vul XSS<br>

![image](https://github.com/user-attachments/assets/1215d19e-2a89-4ebc-9b66-4dfb60444aff)<br>

3. payload bị chèn vào 1 biến nên ko thưc thi đc -> đóng thẻ script trước: </script> <script>alert("xss")</script> -> đc thực thi
<br>

![image](https://github.com/user-attachments/assets/c493b0ad-ae13-4e0e-9cc0-8e26bf1c57f3)<br>

4. chèn payload để lấy in4: </script> <script>alert(document.cookie)</script> -> coolcookie112<br>

![image](https://github.com/user-attachments/assets/b98a4461-4e50-41a2-8125-aa4b61422fd0)<br>
