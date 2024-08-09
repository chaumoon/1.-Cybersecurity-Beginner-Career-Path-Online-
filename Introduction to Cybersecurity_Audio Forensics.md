I. Lý thuyết<br>
1. data đc ẩn bên trong file audio<br>
- có 2 cách:<br>
+ xài tool để giữ file bên trong metadata (deep sound)
+ deep sound: công cụ dựa trên windows để ẩn file bên trong file audio, nó can ẩn or trích xuất file bên trong các file audio<br>

2. data đc ẩn trong wave (sóng)<br>
- trong các wave frame, can kiểm soát các giá trị của nó:<br>
+ frame có nh khung có giá trị top và bottom, can đặt giá trị này thành bất cứ giá trị nào bn muốn
+ xài python script: can tiêm giá trị mong muốn vào audio wave or xây dựng 1 file wave từ giá trị bn muốn
+ https://docs.python.org/3/library/wave.html<br>

- ẩn data trong Wave Spectrogram (phổ sóng)<br>
+ xài spectrum analyzer để hiển thị quang phổ của wave
+ phải đợi đến khi all tệp audio đang đc phát mới tìm đc tin nhắn ẩn trên phổ trừ khi bt time gửi tin nhắn đó
+ xài: https://www.audacityteam.org/ -> nếu file quá dài thì tìm kiếm khó khăn hơn
+ xài tool: sox -> cung cấp all đầu ra file audio ở dang file ảnh, nhưng nó ko hoạt động vs nh loại file audio<br>

II. lap: I love music<br>
1. dùng sox xem quang phổ file <br>

![image](https://github.com/user-attachments/assets/86d0bf35-5ac8-40b3-a6f7-2ea62017dae9)<br>

2. flag: you_are_victorious!
