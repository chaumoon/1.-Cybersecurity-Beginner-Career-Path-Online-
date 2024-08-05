I. Lý thuyết<br>
1. tiêm SQL là gì<br>
- là vul web cho phép attacker truy xuất data nhạy cảm từ app database bằng cách tiêm truy vấn SQL vào 1 trong các chức năng của app để truy xuất data user
- SELECT -> truy xuất data
- FROM -> chỉ định table đc xài
- WHERE -> chỉ định 1 hàng cụ thể của data
- UNION -> kết hợp 2 câu lệnh nhằm lấy data từ các table khác nhau và kết hợp kết quả lại vs nhau
- những gì xuất hiện sau '#' và '--' đều ko đc xử lý<br>

*. PHP xài truy vấn SQL để truy xuất data<br>

![image](https://github.com/user-attachments/assets/6ec9536e-6ece-4b79-964d-a185cf896703)<br>

- mysqli_connect() -> mở 1 kết nối mới tới MySQL database
- mysqli_query() -> thực hiện truy vấn SQL đc cung cấp và trả về k.quả, đồng thời lấy biế kết nối làm tham số
- đôi khi truy vấn SQL ko tĩnh, nó can lấy 1 số tham số truy vấn từ user<br>

*. các loại tiêm SQL attack<br>
- Inband: data đc truy vấn xài cùng 1 kênh dùng để tiêm SQL
- Out-of-band: data đc truy vấn xài kênh khác (vd: mail vs kết quả truy vấn đc tạo và gửi tới tester)
- Blind: lỗi ko hiển thị khi tiêm SQL<br>

*. 1 vài kĩ thuật cho tiêm SQL attack<br>
- Union attack -> kết hợp 2 truy vấn lại thành 1/1 bộ kết quả
- Boolean attack -> xài đk bool để xác minh đk cụ thể là đúng or sai
- Error-based attack -> kĩ thuật buộc database tạo ra lỗi
- Out-of-band-> dùng để truy xuất data khác kênh
- Time delay -> dùng lệnh database để trì hoãn kết quả trong các truy vấn có đk<br>

2. cách để test<br>
*. phát hiện:<br>
- hiểu hành vi app và tìm hiểu khi nào nó tương tác vs database
- 
