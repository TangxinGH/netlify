---
title: apache配置代理
date: 2019-10-21 20:13:01.000
updated: 2019-10-21 20:15:12.000
csdn_url: https://blog.csdn.net/weixin_43531940/article/details/102670963
description: 复制到你的conf后面。重启apache,无法重启说明有错，查看日志。
#代理，不要的话删掉到proxy那里就可以了，上面有相同的模块，是注释掉的
#LoadModule access_compat_module modules/mod_access_compat.so

LoadModule lbmethod_bybusyness_module modules/mod_lbmethod_bybu...
tags: 
categories: 网络
article_id: 102670963
---
﻿
复制到你的conf后面。重启apache,无法重启说明有错，查看日志。
```bash
#代理，不要的话删掉到proxy那里就可以了，上面有相同的模块，是注释掉的
#LoadModule access_compat_module modules/mod_access_compat.so

LoadModule lbmethod_bybusyness_module modules/mod_lbmethod_bybusyness.so

LoadModule lbmethod_byrequests_module modules/mod_lbmethod_byrequests.so

LoadModule lbmethod_bytraffic_module modules/mod_lbmethod_bytraffic.so

LoadModule lbmethod_heartbeat_module modules/mod_lbmethod_heartbeat.so

LoadModule proxy_module modules/mod_proxy.so

LoadModule proxy_connect_module modules/mod_proxy_connect.so

LoadModule proxy_ftp_module modules/mod_proxy_ftp.so

LoadModule proxy_html_module modules/mod_proxy_html.so

LoadModule proxy_http_module modules/mod_proxy_http.so

LoadModule xml2enc_module modules/mod_xml2enc.so

ProxyRequests On

<Proxy *>

    Require all granted

</Proxy>
```


浏览器设置代理，localhost:8080你的端口号![在这里插入图片描述](http://img.yayi.site/csdn/2019102120135066.png-watermaskStyle)
能访问就成功
