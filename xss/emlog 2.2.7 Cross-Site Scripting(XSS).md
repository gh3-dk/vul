# emlog<=pro-2.2.7 存储型跨站脚本攻击(XSS)
## Description
    The system Client doesn't properly sanitise POST parameter, which result into a Stored Cross-Site Scripting(XSS).
## Vendor Homepage
    https://www.emlog.net/
    https://github.com/emlog/emlog

## Author
    xiahao@webray.com.cn inc  
## Proof of Concept
1,在网站注册账号并登录
![f9b5fa49cd60693d1a37c2332802a4a4.png](https://github.com/gh3-dk/vul/blob/main/images/emlog1.png)
2、添加文章并编写攻击代码，然后提交
```
<script>alert(123);</script>
```
![dd43272e1ff2661eac1c0ca2fef898b5.png](../_resources/dd43272e1ff2661eac1c0ca2fef898b5.png)
3,管理员在审核时，没注意到恶意代码，不小心审核通过，别的用户或者管理员每次在主页浏览这篇博客时就会触发XSS攻击
![986be6d884d29c3bb6568ed37e2004cf.png](../_resources/986be6d884d29c3bb6568ed37e2004cf.png)
![03cd7b4163dd1ff13d13f33761b2412e.png](../_resources/03cd7b4163dd1ff13d13f33761b2412e.png)
