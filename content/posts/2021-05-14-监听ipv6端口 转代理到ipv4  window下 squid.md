ccproxy 不支持ipv6
squid 支持，默认同时监听ipv6/4  ，然而我却无法访问？？？ipv6的？？

```bash
ERROR
The requested URL could not be retrieved
当尝试取回该 URL 时遇到下面的错误：http://118.190.57.133:8080/

访问被拒绝。

Access control configuration prevents your request from being allowed at this time. Please contact your service provider if you feel this is incorrect.

缓存服务器的管理员 webmaster.


已由 localhost (squid/3.5.28) 生成 Sat, 07 Dec 2019 12:24:57 GMT


```
==在代理服务器上 设置dns的问题，或者多设置几个dns==

,一208.67.222.222谷歌的公用DNS服务器  导致无法上网？？
看来还是得有错误信息才能解决问题  查看端口号是否监听了ipv6 [::]: 这种样子的 
tcping 工具
也有可能是我开了两个的原因
### 二
也可以用nginx
nginx 监听 

        listen      0.0.0.0:80;
        listen      [::]:80;
    }
    应该
    因为ipv6地址相对固定，校园网 分配到几乎是一样的。但是无法上网而已
nginx 无法https正向代理 ，我试不行，别人好像行
正向和返向，感觉是有无上级关系
别人：
正向代理：

     所谓正向代理就是内网服务器主动要去请求外网的地址或服务，所进行的一种行为。内网服务---访问--->外网

2）反向代理：

    所谓反向代理就是外网要访问内网服务而进行的一种行为。 外网----请求--->内网服务

    
