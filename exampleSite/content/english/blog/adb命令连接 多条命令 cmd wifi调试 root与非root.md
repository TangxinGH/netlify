---
title: adb命令连接 多条命令 cmd wifi调试 root与非root
date: 2020-06-28 12:00:31.000
updated: 2020-06-28 12:00:31.000
csdn_url: https://blog.csdn.net/weixin_43531940/article/details/106996097
description: adb uninstall cn.edu.glut.llk&amp;&amp;adb install app-debug.apk&amp;&amp;adb shell am start -n cn.edu.glut.llk/cn.edu.glut.llk.MainActivity


&amp;&amp;



tags: adb,cmd,多条
categories: win10,andriod
article_id: 106996097
---
﻿```c
adb uninstall cn.edu.glut.llk&&adb install app-debug.apk&&adb shell am start -n cn.edu.glut.llk/cn.edu.glut.llk.MainActivity
```

> &&
> 

adb 局域网调试。首先手机手动开启端口。
方法一：==不需要root ，但需要数据线==，先数据线cmd开启 tcpip模式。相当于在手机上开启了端口。拨掉数据线，就可以了。==但手机重启后，得重新数据线一遍。==

方法二：root 权限开启tcpip模式。直接在手机上开启。百度命令。

