I. Lý thuyết<br>
- tool cần thiết: https://addons.mozilla.org/en-US/firefox/addon/cookie-editor/<br>

1. Cookies là gì<br>
- cookie là data mà browser lưu trữ trong các file text nhỏ trên máy tính
- cookie giúp giải quyết vấn đề: ghi nhớ in4 user
- khi login vào web ko cần nhập lại in4 vì nó đã đc lưu trong cookie, cookie được lưu dưới dạng 1 cặp name-value: username = user
- khi browser yêu cầu 1 page từ server, cookie thuộc page sẽ đc thêm vào yêu cầu -> server lấy đc in4 cần thiết để nhớ user<br>

2. Thao tác cookie <br>
- javascript can tạo, đọc, xóa cookie với thuộc tính: document.cookie<br>

*. tạo cookie<br>
- tạo như sau: document.cookie = "username = user";
- can thêm ngày hết hạn (UTC time) vì theo mặc định nó sẽ hết hạn khi browser đóng: document.cookie = "username = user; expires = Thu, 18 Dec 2013 12:00:00 UTC";
- với tham số path, bn can cho browser bt cookie thuộc path nào vì theo mặc định cookie thuộc page hiện tại: document.cookie = "username = user; expires = Thu, 18 Dec 2013 12:00:00 UTC; path = /";<br>

*. đọc cookie<br>
- đọc bằng: var x = document.cookie;<br>

*. thay đổi cookie<br>
- giống y như tạo:  document.cookie = "username = user; expires = Thu, 20 Dec 2013 12:00:00 UTC; path = /";<br>

*. xóa cookie<br>
- cài đặt tham số ngày hết hạn thành ngày đã qua là được:  document.cookie = "username = user; expires = Thu, 1 Dec 2013 12:00:00 UTC; path = /";<br>

*. hàm để set cookie<br>
- tạo hàm lưu trữ tên ng truy cập vào biến cookie -> VD:<br>
```
function setCookie(cname, cvalue, exdays) {
    var d = new Date();
    d.setTime(d.getTime() + (exdays*24*60*60*1000));
    var expires = "expires=" + d.toUTCString();
    document.cookie = cname + "=" + cvalue + ";" + expires + ";path=/";
}
```

- hàm bao gồm tên cookie, giá trị cookie và số ngày cho đến khi cookie hết hạn -> trong hàm sẽ đặt giá trị cụ thể từng biến<br>

II. lap: Admin has the power<br>
1. chặn truy cập thu được phản hồi -> có tài khoản: user:support password:x34245323<br>

![image](https://github.com/user-attachments/assets/96c22402-1a4c-4310-9ccd-011c0cb98e1a)<br>

2. check cookie đã đc set ở phản hồi<br>

![image](https://github.com/user-attachments/assets/555a4f9b-d76b-46bb-aaf0-35a13c74fcd6)<br>

3. sửa đổi cookie -> nhận đc flag<br>

![image](https://github.com/user-attachments/assets/a363689c-46d2-4e3c-821f-ea24e04f2b1f)<br>
