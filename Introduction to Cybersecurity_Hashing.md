I. Lý thuyết<br>
1. hàm băm (hash)<br>
- là hàm 1 chiều, cung cấp 1 đầu ra duy nhất cho 1 đầu vào
- các hàm hash đc xem là an toàn giờ đây đã xảy ra xung đột <-> 2 đầu vào cho cùng 1 đầu ra<br>

2. các loại hash<br>
- MD5:<br>
+ mã hóa 1 chuỗi và chuyển nó thành dấu vân tay 128 bit
+ thg xài như 1 checksum để xác minh tính toàn vẹn của data
+ có nh lỗ hổng xung đột hàm băm nhưng vẫn đc xài rộng rãi trên thế giới<br>

- SHA-2:<br>
+ là hàm băm mật mã, thay đổi đáng kể so vs HSA-1
+ gồm 6 hàm băm vs các giá trị băm là 224, 256, 384 or 512 bit: SHA-224, SHA-256, SHA-384, SHA-512, SHA-512/224, SHA-512/256.<br>

3. băm chuỗi<br>
- là 1 số or chuỗi đc tạo bằng thuật toán chạy trên text or data
- mỗi hash phải là duy nhất cho mỗi text or data
- can xài tool dòng lệnh or công cụ trực tuyến để băm<br>

4. băm file<br>
- cần thiết trong an ninh mạng: <br>
+ xác minh file để xác minh tính toàn vẹn of file mt
+ lm bằng chứng cho các cuộc điều tra tấn công mạng
+ vấn đề kĩ thuật khác
- để băm trong windows: Get-FileHash + path_of_file -> mặc định xài SHA-2 256
- trong linux xài các lệnh phù hợp để băm chuỗi<br>

-> đáng tin khi cho bt khi nào 2 tệp giống nhau, hữu ích cho phân tích bảo mật trong hoạt động như share chỉ số về sự xâm nhập (IOC) hay săn lùng mối đe dọa<br>

II. lap: Hash3rror<br>
1. xét hàm băm: 77be5d24ed2e3e590045e1d6o7e84i50d2799c19f48ede46804a8734e287df120f<br>
- ở dang hex nhưng lại có kí tự 'o' và 'i' -> loại
- thu đc: 77be5d24ed2e3e590045e1d67e8450d2799c19f48ede46804a8734e287df120f <br>

2. dùng tool để xác định loại hàm băm đc xài<br>
- https://hashes.com/en/tools/hash_identifier<br>

![image](https://github.com/user-attachments/assets/ea77e005-fef1-4dcc-8184-7ec252e75980)<br>

3. giải mã hàm băm -> s3cr3tpassword<br>

![image](https://github.com/user-attachments/assets/565c6129-1eb0-4c83-b0ad-0286b3dff412)<br>

4. mã hóa lại kết quả với hàm băm sha-1 -> 83874343435092cb681c0d558a84bfeb389c32ed<br>

![image](https://github.com/user-attachments/assets/dccc7535-30d9-4171-afd1-f037bf81d8b6)<br>
