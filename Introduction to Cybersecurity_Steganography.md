I. Lý thuyết<br>
1. steganograpy là gì<br>
- là nghệ thuật và khoa học nhúng 1 tin nhắn bí mật vào 1 tin nhắn bìa theo cách mà ko ai ngoài ng gửi và ng nhận dự định nghi ngờ về sự tồn tại của nó<br>

2. steganography khác gì với cryptography<br>
- cùng mục đích là bảo vệ tin nhắn or in4 của bên thứ 3
- tuy nhiên lại xài cơ chế bảo vệ khác nhau
- cryptography thay đổi ciphertext information khiến ko thể hiểu đc nếu ko có key giải mã, ai chặn đc tin nhắn đã mã hóa này cx can thấy rằng 1 loại mã hóa nào đó đã đc xài
- steganography ko thay đổi format in4 mà nó che giấu sự tồn tại của tin nhắn<br>

3. kĩ thuật steganography<br>
*. Image Steganography<br>
- là ẩn data bằng cách lấy đối tượng bìa lm background
- trong digital steganography, ảnh đc xài rộng rãi lm nguồn bìa vì biểu diễn kĩ thuật số của ảnh chứa lượng lớn các bit
- có 1 số cách để ẩn data vs hình ảnh:<br>
+ Least Significant Bit Insertion (chèn bit ít quan trọng nhất)
+ Masking and Filtering: che giấu và lọc
+ Redundant Pattern Encoding: mã hóa mẫu dự phòng
+ Encrypt and Scatter: mã hóa và phân tán<br>

*. Audio Steganography<br>
- thông điệp bí mật đc nhúng vào tín hiệu âm thanh lm thay đổi chuỗi nhị phân of tệp âm thanh tương ứng
- khó khăn hơn nh phương pháp khác
- các phương pháp:<br>
+ Least Significant Bit Encoding
+ Parity Encoding: mã hóa chẵn lẻ
+ Phase Coding: mã hóa pha
+ Spread Spectrum: trải phổ<br>

3. tool<br>
- Stegsolve: chuyển đổi ảnh 1 cách tương tác và xem các bảng màu riêng biệt
- SonicVisualiser: hiển thị file audio ở dạng sóng, hiển thị các biểu đô phổ
- DeepSound Audio stego: steghide để mã hóa và ẩn data<br>

II. lap: Greeks<br>
The art of hiding messages or information inside other image / text or data<br>

-> Steganography
