I. Lý thuyết<br>
1. giới thiệu về JPG<br>
- là 1 loại format ảnh, format ảnh kĩ thuật số đc dùng rộng rãi nhất
- sử dụng nén có tổn hao để nén data hình ảnh
- khi nén ở mức thấp -> mất lượng nhỏ data và có đc hình ảnh chất lượng cao
- khi xài mức nén cao -> mất nh data hơn và chất lượng hình ảnh thấp
- thg đc xài trong máy ảnh kĩ thuật số và thiết bị chụp ảnh<br>

2. biểu diễn meta data<br>
- 1 file JPG bao gồm 2 format phụ: JPG/Exif:<br>
+ JPG: gồm 1 chuỗi các segment và header, mỗi header bắt đầu bằng byte 0xff theo sau là 1 header khác để chỉ định header viết tắt của gì
+ Exif: chứa 1 vài in4 về nguồn của jpg (thg là máy ảnh kĩ thuật số) or in4 về việc tạp jpg (time, địa điểm)<br>

3. JPG marker/header phổ biến<br>
- 0xFF 0xD8(SOI):<br>
+ byte đầu tiên (bagic byte của jpg)
+ nếu ko có nó -> file ko thể thực thi
+ chỉ có 2 byte ko có data bổ sung<br>
- 0xFF 0xE0(APP0):<br>
+ app segment 0
+ xác định file nếu nó là JFI, JPEG ảnh or JPEG động
+ có 1 vài in4 về file version
+ file can hoạt động mà ko cần nó<br>
- 0xFF 0xDB(DQT):<br>
+ xác định bảng lượng tử hóa
+ chứa data rất nhạy cảm, bất kì thay đổi nào trên nó cx ảnh hg đến file, đôi khi khiến file ko hoạt động
+ 1 file can chứa nh hơn 1 DQT<br>
- 0xFF 0xC2(SOF2):<br>
+ là 1 trong những điểm bắt đầu of frame marker, là điểm bắt đầu của frame 2, có 4 điểm bắt đầu của frame marker và có 1 file đc xài trong số đó
+ là 1 trong những header quan trọng trên jpg, điều khiển việc biểu diễn data như chiều dài và chiều rộng,..
+ mọi thay đổi sẽ ảnh hg đến ảnh, đôi khi nó ko hoạt động, đôi khi hiển thị 1 cách kì lạ phụ thuộc vào byte đã thay đổi<br>
- 0xFF 0xDA(SOS):<br>
+ bắt đầu of Scan, chứa data sẽ đc hiển thị trên ảnh
+ bất kì sự thay đổi lớn nào cx dẫn đến hỏng hình ảnh<br>
- 0xFF 0xD9(EOI):<br>
+ kết thúc của hình ảnh
+ bất kì sự thay đổi nào nếu ko có data bổ sung thì ko ảnh hg đến ảnh, nếu có thì sẽ ảnh hưởng<br>

II. lap: Keep it Simple<br>
1. mở source và phát hiện 3 file ảnh<br>

![image](https://github.com/user-attachments/assets/74c37f2d-2c8a-4c4c-ac07-bd0882b4a709)<br>

2. exiftool cả 3 ảnh -> flag: {S1mpl3sty_i$_th_@nswer}<br>

![image](https://github.com/user-attachments/assets/34c8b961-8190-4375-a5f2-9adeb2c77462)<br>
