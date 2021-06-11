---
title: mysql导入报错 [Err] 1273 - Unknown collation: ‘utf8mb4_0900_ai_ci‘
date: 2019-11-16 07:57:57.000
updated: 2019-11-16 08:00:40.000
csdn_url: https://blog.csdn.net/weixin_43531940/article/details/103094802
description: 首先查看你服务器的字符排序规则
然后把对应的sql文件中，替换成相应的字符集
我在na vcat中设置好像没有用



tags: 
categories: 数据库
article_id: 103094802
---
﻿
首先查看你服务器的字符排序规则
然后把对应的sql文件中，替换成相应的字符集
我在na vcat中设置好像没有用

![在这里插入图片描述](http://img.yayi.site/csdn/20191116075739823.png-watermaskStyle)
