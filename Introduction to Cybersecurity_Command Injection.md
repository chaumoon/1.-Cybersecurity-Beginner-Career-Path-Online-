I. Lý thuyết<br>
1. tiêm lệnh là gì<br>
- là vul web mà attacker can chèn lệnh OS vào app, lệnh sẽ đc thực thi trên server lưu trữ app web và kiểm soát hoàn toàn app web cx như các thành phần của app đó<br>

2. cách để test<br>
- phải phát hiện all khu vực input và hiểu app lấy data gì từ user
- VD: app lấy file từ user và xóa nó<br>

![image](https://github.com/user-attachments/assets/0b690656-2423-46cf-8f9f-1341745a20f9)<br>

- code đã lấy tham số GET từ user và thực thi nó bằng hàm system
- code php<br>
+ print(): in 1 chuỗi trên page
+ isset(): check xem intput có trống ko
+ system(): thực thi input và xuất output<br>
- VD: http:/example.com/delete.php?filename=test.txt;id<br>
+ ';': kết thúc khối code
+ id: lệnh linux hiển thị all chi tiết system user: uid=33(www-data) gid=33(www-data) groups=33(www-data)<br>
- hoặc liệt kê: http:/example.com/delete.php?filename=test.txt;ls -la
- các dấu phân cách lệnh can xài để chèn lệnh OS:<br>
+ &
+ &&
+ |
+ ||
+ ;
+ Newline (0x0a or \n)
+ ` command `
+ $( command)<br>

3. phòng tránh<br>
- dọn sạch input trước khi nó xử lý 1 trong các chức năng sau:<br>
- Java
+ Runtime.exec()<br>

- C/C++
+ system
+ exec
+ ShellExecute<br>

- Python
+ exec
+ eval
+ os.system
+ os.popen
+ subprocess.popen
+ subprocess.call<br>

- PHP
+ system
+ shell_exec
+ exec
+ proc_open
+ eval<br>

- cần tạo 1 list từ chối để loại bỏ các kí tự đặc biệt can chèn lệnh:<br>
+ windows: ( ) < > & * ‘ | = ? ; [ ] ^ ~ ! . ” % @ / \ : + , `
+ linux: { } ( ) > < & * ‘ | = ? ; [ ] $ – # ~ ! . ” %  / \ : + , `<br>

4. tool<br>
- https://portswigger.net/
- khai thác và tiêm lệnh OS All-in-One 1 cách tự động: https://github.com/commixproject/commix<br>

II. lap: Newsletter<br>
1. dùng fg&pwd&hjk@gmail.com -> pwd để show thư mục hiện tại -> check xem lệnh có hoạt động ko<br>

![image](https://github.com/user-attachments/assets/201efba9-de9c-47ac-84b5-bf0a502549dc)<br>

2. thử với lệnh ls -> hgdr64.backup.tar.gz<br>

![image](https://github.com/user-attachments/assets/80d59389-39bb-4eab-9d84-d1d4ffcf7f50)<br>
