---
title: java.lang.ClassNotFoundException: com.mysql.cj.jdbc.Driver 	at java.net.URLClassLoader.findClass(URL
date: 2019-10-16 22:50:35.000
updated: 2019-10-16 22:55:52.000
csdn_url: https://blog.csdn.net/weixin_43531940/article/details/102596546
description: 如果是少jar包的话，idea,

打开cmd查看你的mysql版本
添加maven管理
浏览器打开：mysql，包，仓库
下载对应版本包
或者：

复制：

到你项目的pom中


tags: 
categories: javaweb
article_id: 102596546
---
﻿如果是少jar包的话，idea,
![在这里插入图片描述](http://img.yayi.site/csdn/20191016224859650.png-watermaskStyle)
打开cmd查看你的mysql版本
添加maven管理
浏览器打开：[mysql，包，仓库](http://mvnrepository.com/artifact/mysql/mysql-connector-java)
下载对应版本包
或者：
![在这里插入图片描述](http://img.yayi.site/csdn/20191016225234465.png-watermaskStyle)

复制：
![在这里插入图片描述](http://img.yayi.site/csdn/20191016225525196.png-watermaskStyle)
到你项目的pom中

