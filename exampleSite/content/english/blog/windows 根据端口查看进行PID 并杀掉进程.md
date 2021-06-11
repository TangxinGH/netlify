---
title: windows 根据端口查看进行PID 并杀掉进程
date: 2019-11-16 08:38:33.000
updated: 2019-11-16 08:38:36.000
csdn_url: https://blog.csdn.net/weixin_43531940/article/details/103094881
description: 首先用netstat -ano | find “端口号”查出进程号
2. takslist 查询当前的进行
3. . 如何杀死进程呢  tasklist /pid ${xx}
发现不行呢，权限不够，用管理员权限运行cmd，发现又报错了，说要强制执行才可以，加上-F

...
tags: 
categories: win10
article_id: 103094881
---
﻿ 首先用netstat -ano | find “端口号”查出进程号
2. takslist 查询当前的进行
3. . 如何杀死进程呢  tasklist /pid ${xx}


https://www.cnblogs.com/qianjinyan/p/10772540.html
发现不行呢，权限不够，用管理员权限运行cmd，发现又报错了，说要强制执行才可以，加上-F


