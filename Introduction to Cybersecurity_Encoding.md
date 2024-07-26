I. Lý thuyết<br>
1. encode và decode<br>
- encode: chuyển đổi 1 chuỗi thành định dạng chuyên biệt để truyền tải
- decode: tiến trình ngược của encode
- các sơ đồ mã hóa khác nhau đc xài để đảm bảo cơ chế xử lý an toàn các kí tự bất thường và dữ liệu nhị phân can xuất hiện
- mã hóa xài trong giao tiếp và lưu trữ data, ko xài để truyền data nhạy cảm<br>

2. các loại sơ đồ encode<br>
- URL encode<br>
+ URl chỉ chứa kí tự ascii, nếu chứa kí tự ngoài thì cần mã hóa
+ VD: # = %23<br>

- HTML encode<br>
+ khi bn tấn công web thì nó xài để tìm cross-site scripting vul
+ khi app trả về input user chưa đc sửa đổi trong phản hồi -> web dễ vul
+ nếu các kí tự nguy hiểm đc mã hóa trong HTML -> an toàn
+ như mã hóa URL, 1 số kí tự có nghĩa cụ thể nên cần mã hóa nếu chúng cần được sử dụng mà không bao hàm ý nghĩa của chúng.
+ VD: > = %gt;<br>

- Base-64 encode<br>
+ thể hiện 1 cách an toàn data nhị phân, mã hóa tệp đính kè mail để truyền an toàn qua SMTP
+ mã hóa in4 login user trong xác thực HTTP cơ bản
+ dùng 4 kí tự ascii để mã hóa 24 bit data, chia 24 bit thành 4 số 6 bit -> mỗi số 6 bit can đại diện cho 64 giá trị khả dĩ, mỗi giá trị khả dĩ tương ứng 1 kí tự ascii<br>

- hex và unicode encode -> mục đích là truyền data hiệu quả<br>

II. lap: who am i?<br>
1. login bừa 1 acc -> tìm đc 1 acc Guest<br>

![image](https://github.com/user-attachments/assets/64805e34-cd7c-46c9-a36d-3ec35c977c0c)<br>

2. login acc tìm đc và tìm đc cookie: Set-Cookie: Authentication=bG9naW49R3Vlc3Q<br>

![image](https://github.com/user-attachments/assets/fc1c20df-2608-45b0-bb89-7289b1b13757)<br>

3. giải mã cookie: -> login=Guest<br>

![image](https://github.com/user-attachments/assets/8b5707bd-7c4e-4676-9367-e76052dee4fd)<br>

4. mã hóa acc admin và sửa cookie: bG9naW49YWRtaW4=<br>

![image](https://github.com/user-attachments/assets/55461ae2-2e03-4319-8898-daab49c5357e)<br>

5. gửi yêu cầu và nhận flag: FLag{B@D_4uTh1Nt1C4Ti0n}<br>

![image](https://github.com/user-attachments/assets/eb1c256b-73e0-4ea3-9f15-573ec22a2268)
