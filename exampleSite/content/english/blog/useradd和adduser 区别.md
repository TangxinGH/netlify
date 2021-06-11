---
title: useradd和adduser 区别
date: 2020-06-07 12:40:25.000
updated: 2020-06-07 12:40:25.000
csdn_url: https://blog.csdn.net/weixin_43531940/article/details/106600088
description: 首先在redhat中是一样的。
在Slackware中，adduser指令是个script程序，利用交谈的方式取得输入的用户帐号资料，然后再交由真正建立帐号的useradd命令建立新用户，如此可方便管理员建立用户帐号。在Red Hat Linux中， adduser命令 则是useradd命令的符号连接，两者实际上是同一个指令。
在其它系统就不一定一样了。
如ubutun中家目录有没有创建的区别的。

...
tags: 
categories: Linux
article_id: 106600088
---
﻿
# 首先在redhat中是一样的。
在Slackware中，adduser指令是个script程序，利用交谈的方式取得输入的用户帐号资料，然后再交由真正建立帐号的useradd命令建立新用户，如此可方便管理员建立用户帐号。在Red Hat Linux中， adduser命令 则是useradd命令的符号连接，两者实际上是同一个指令。

# 在其它系统就不一定一样了。
如ubutun中家目录有没有创建的区别的。
