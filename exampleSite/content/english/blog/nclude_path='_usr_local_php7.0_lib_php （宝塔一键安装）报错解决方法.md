---
title: nclude_path='/usr/local/php7.0/lib/php （宝塔一键安装）报错解决方法
date: 2019-11-16 09:07:19.000
updated: 2019-11-16 09:07:19.000
csdn_url: https://blog.csdn.net/weixin_43531940/article/details/103095042
description: https://blog.csdn.net/qq_42154707/article/details/84238489
我的还改了路径才行

之后发生了
file_put_contents(/www/server/apache/htdocs/runtime/temp/a008e8028bd7ed1266d50be7e593dded.php): failed to open stream: Permi...
tags: 
categories: php
article_id: 103095042
---
﻿[https://blog.csdn.net/qq_42154707/article/details/84238489](https://blog.csdn.net/qq_42154707/article/details/84238489)
我的还改了路径才行
![在这里插入图片描述](http://img.yayi.site/csdn/20191116085523312.png-watermaskStyle)


之后发生了
file_put_contents(/www/server/apache/htdocs/runtime/temp/a008e8028bd7ed1266d50be7e593dded.php): failed to open stream: Permission denied
开启debug模式

第一路径要对
[https://blog.csdn.net/zch501157081/article/details/51981320/](https://blog.csdn.net/zch501157081/article/details/51981320/)

权限，我的是linux
[https://blog.csdn.net/lxw1844912514/article/details/100029521](https://blog.csdn.net/lxw1844912514/article/details/100029521)
在宝塔LInux里改方便
之前改路径和防跨站好像没意义啊，。。。
