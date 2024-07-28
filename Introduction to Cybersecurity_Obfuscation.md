I. Lý thuyết<br>
1. Obfuscation & Deobfuscation (che giấu và giải mã)<br>
- Obfuscation: quá trình chuyển script thành dạng khó hiểu hơn nhưng trả về kết quả tg tự. có nh phg pháp che dấu -> nh tool
- Deobfuscation: đảo ngược của Obfuscation, chuyển script từ dạng khó đọc thành dễ đọc hơn<br>

2. tại sao phải dùng Obfuscation<br>
- ngăn chặn ng khác ăn cắp code
- tránh attacker hiểu chức năng của script và tận dụng nó
- bỏ qua WAF và hệ thống phát hiện bảo mật khỏi việc lọc or phart hiện pyload của bn<br>

3. javascript Obfuscation<br>
- có 1 số cách, 1 trong số đó là loại bỏ khoảng trắng (rút gọn mã) -> htg xài và giảm kích thước script<br>

4. Tool<br>
- JSF: http://www.jsfuck.com/
- -> viết bất kì script thành 6 kí tự []()!+
- Packer Obfuscation: https://www.cleancss.com/javascript-obfuscate/index.php
- https://obfuscator.io/
- VD: https://aem1k.com/
- -> all text và kí hiệu script sẽ đc lưu trữ trong list or từ điển, sẽ đc khôi phục và xây dựng lại trong quá trình thực thi
- JS deobfuscation Tools: các công cụ trực tuyến:<br>
+ giải mã JS nâng cao thông qua đánh giá 1 phần: https://mindedsecurity.github.io/jstillery/
+ http://deobfuscatejavascript.com/
+ https://beautifier.io/<br>

II. lap<br>
1. Modify Code<br>
Change code from one form to another to prevent attacker from understanding it<br>

-> Obfuscation<br>

2. Iam Legend<br>
- log bừa 1 acc -> tìm đc 1 đoạn script đã bị mã hóa<br>

![image](https://github.com/user-attachments/assets/fe6c7959-36a4-48eb-9c51-4070171d398c)<br>

- dùng tool: [http://www.jsfuck.com/](https://lelinhtinh.github.io/de4js/) để giải mã -> <br>

![image](https://github.com/user-attachments/assets/f7b390af-2ae5-4e88-8692-48d280a56600)<br>

```
String.fromCharCode(102, 117, 110, 99, 116, 105, 111, 110, 32, 99, 104, 101, 99, 107, 40, 41, 123, 10, 10, 118, 97, 114, 32, 117, 115, 101, 114, 32, 61, 32, 100, 111, 99, 117, 109, 101, 110, 116, 91, 34, 103, 101, 116, 69, 108, 101, 109, 101, 110, 116, 66, 121, 73, 100, 34, 93, 40, 34, 117, 115, 101, 114, 34, 41, 91, 34, 118, 97, 108, 117, 101, 34, 93, 59, 10, 118, 97, 114, 32, 112, 97, 115, 115, 32, 61, 32, 100, 111, 99, 117, 109, 101, 110, 116, 91, 34, 103, 101, 116, 69, 108, 101, 109, 101, 110, 116, 66, 121, 73, 100, 34, 93, 40, 34, 112, 97, 115, 115, 34, 41, 91, 34, 118, 97, 108, 117, 101, 34, 93, 59, 10, 10, 105, 102, 40, 117, 115, 101, 114, 61, 61, 34, 67, 121, 98, 101, 114, 34, 32, 38, 38, 32, 112, 97, 115, 115, 61, 61, 32, 34, 84, 97, 108, 101, 110, 116, 34, 41, 123, 97, 108, 101, 114, 116, 40, 34, 32, 32, 32, 32, 32, 32, 32, 32, 32, 32, 32, 32, 32, 32, 32, 32, 32, 32, 32, 32, 32, 32, 67, 111, 110, 103, 114, 97, 116, 122, 32, 92, 110, 32, 70, 108, 97, 103, 58, 32, 123, 74, 52, 86, 52, 95, 83, 99, 114, 49, 80, 116, 95, 49, 83, 95, 83, 48, 95, 68, 52, 77, 78, 95, 70, 85, 78, 125, 34, 41, 59, 125, 32, 10, 101, 108, 115, 101, 32, 123, 97, 108, 101, 114, 116, 40, 34, 119, 114, 111, 110, 103, 32, 80, 97, 115, 115, 119, 111, 114, 100, 34, 41, 59, 125, 125)
```

- ném vào chatgpt -> thu được kết quả: Flag: {J4V4_Scr1Pt_1S_S0_D4MN_FUN}<br>

![image](https://github.com/user-attachments/assets/fddd8f72-c34f-41bd-b058-4cc3c99766cf)<br>
