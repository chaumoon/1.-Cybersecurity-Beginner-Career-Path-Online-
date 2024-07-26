I. Lý thuyết<br>
1. JavaScript là gì<br>
- là ngôn ngữ dùng trong dự án phát triển front-end, back-end và full-stack
- là ngôn ngữ script phía máy khách giúp web trở nên tg tác và năng động hơn
- trong pentest cần học tốt về javascript để phân tích web app code và tìm lỗ hổng phía máy khách (XSS, CFRS)
- có thể viết javascript trong page html
- khi thực thi nó sẽ hiển thị hộp alert (cảnh báo)
- khi check DOM XSS, nên theo dõi nguồn (Sources) và phần chìm (Sinks) trong page<br>
+ Sources: nơi data đầu vào đc submit
+ nơi data đầu vào đc thực thi or in<br>
- target của bn sẽ luôn thực thi JS được chèn để lấy data nhạy cảm or ép user thực hiện hành động ko mong muốn bằng cách gửi cho họ các liên kết độc hại chứa mã JS độc hại<br>

II. lap: This is Sparta<br>
1. phản hồi đoạn code thu được đoạn mã javascript<br>

![image](https://github.com/user-attachments/assets/4bec6e2b-f290-43b6-a27a-d7d75dfbdf8a)<br>

```
var _0xae5b = [ "\x76\x61\x6C\x75\x65", "\x75\x73\x65\x72", "\x67\x65\x74\x45\x6C\x65\x6D\x65\x6E\x74\x42\x79\x49\x64", "\x70\x61\x73\x73", "\x43\x79\x62\x65\x72\x2d\x54\x61\x6c\x65\x6e\x74", "\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x43\x6F\x6E\x67\x72\x61\x74\x7A\x20\x0A\x0A", "\x77\x72\x6F\x6E\x67\x20\x50\x61\x73\x73\x77\x6F\x72\x64" ];
function check()
{
    var _0xeb80x2 = document[_0xae5b[2]](_0xae5b[1])[_0xae5b[0]];
    var _0xeb80x3 = document[_0xae5b[2]](_0xae5b[3])[_0xae5b[0]];
    if (_0xeb80x2 == _0xae5b[4] && _0xeb80x3 == _0xae5b[4])
    {
        alert(_0xae5b[5]);
    }
    else
    {
        alert(_0xae5b[6]);
    }
}
```

2. dịch ngược code -> đoạn code so sánh user và pass nếu cả 2 bằng Cyber-Talent thì hiện thông báo đúng; ngược lại hiện thông báo lỗi<br>

- dùng tool: https://kt.gy/tools.html#conv/value -> chuyển mã hex thành chữ -> đọc code

![image](https://github.com/user-attachments/assets/75a3357a-4a01-4463-b0db-da513d3c692d)<br>

![image](https://github.com/user-attachments/assets/d60c81f3-45a6-4397-9f45-7bfdfa4cd583)<br>

-> {J4V4_Scr1Pt_1S_Aw3s0me}
