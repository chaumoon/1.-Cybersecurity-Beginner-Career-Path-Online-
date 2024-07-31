I. Lý thuyết<br>
1. Directory Traversal (truyền tải thư mục) là gì<br>
- là web vul nhằm truy cập data đc lưu trữ bên ngoài root folder của web app
- vul này can cho phép attacker truy cập vào mã nguồn của app<br>

2. cách để test<br>
- tìm all phần của app chấp nhận nội dung từ user: HTTP GET, POST queries, file uploads, and HTML forms.<br>
+ check xem có bất kì tham số request nào can xài cho các hoạt động liên quan đến file ko: e.g http://example.com/getUserProfile.php?item=up.html
+ check bất kì cookie nào đc xài để tạo page/template động: e.g Cookie: USER=1826cc8f; read=example.php<br>
- xài các kĩ thuật thông thg<br>
+ để test thành công vul, cần có kiến thức về system đang đc test và vị trí của các file đc yêu cầu: e.g http://example.com/getUserProfile.php?item=../../../../etc/passwd
+ cookie cx vậy: e.g Cookie: USER=1826cc8f; read=../../../../etc/passwd
+ bao gồm cả file và script nằm bên ngoài web: e.g http://example.com/index.php?file=http://test.com/readme.txt<br>
- mỗi OS xài 1 dấu phân cách đg dẫn khác nhau
- nên thử nh cơ chế mã hóa kí tự trong khi test<br>

3. Impact<br>
- lỗ hổng này cho phép attacker đọc mã nguồn web app -> lộ các vul khac or data bí mật can ảnh hưởng đến user công ty hay thậm chí là đọc tệp máy chủ<br>

4. phong ngừa<br>
- cần lọc bất kì data nào từ tham số đầu vào<br>

5. tool<br>
- https://portswigger.net/
- brute-force thư mục: https://wiki.owasp.org/index.php/Category:OWASP_DirBuster_Project
- https://github.com/xmendez/wfuzz/blob/master/wordlist/Injections/Traversal.txt<br>

II. lap: bean<br>
1. dùng tool phân tích url và tìm ra đc 1 url mới chứa các file<br>

![image](https://github.com/user-attachments/assets/0fde815e-ff2e-480c-9064-52160e5315ea)<br>

2. tiếp tục phân tích url mới <br>

![image](https://github.com/user-attachments/assets/acf9da53-facd-494e-9cda-b73717dd02f4)<br>

3. check hết các thư mục và file để tìm file flag -> ko có -> quay lại thư mục hiện tại<br>

![image](https://github.com/user-attachments/assets/79603f50-9c19-4117-825a-5501eb22c08c)<br>

4. check thư mục để tìm file flag<br>

![image](https://github.com/user-attachments/assets/5f94453a-a5dc-48a8-aec3-740d95916f68)<br>

5. tải file về và lấy flag: FLAG{Nginx_nOt_aLWays_sEcUre_bY_The_waY}<br>

![image](https://github.com/user-attachments/assets/aa6f4290-c2c5-4390-ac97-e06ee2f00508)<br>
