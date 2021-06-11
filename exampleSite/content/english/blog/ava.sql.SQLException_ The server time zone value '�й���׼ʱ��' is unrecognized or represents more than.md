---
title: ava.sql.SQLException: The server time zone value '�й���׼ʱ��' is unrecognized or represents more than
date: 2019-10-16 22:58:24.000
updated: 2019-10-16 22:58:24.000
csdn_url: https://blog.csdn.net/weixin_43531940/article/details/102596653
description: mysql连接要指定时间区域地域：
//static final String DB_URL = “jdbc:mysql://localhost:3306/你的数据库?useSSL=false&amp;serverTimezone=UTC”;


tags: 
categories: javaweb
article_id: 102596653
---
﻿，版本不同，或者你连接数据库的url有问题，mysql连接要指定时间区域地域：
//static final String DB_URL = "jdbc:mysql://localhost:3306/你的数据库?useSSL=false&serverTimezone=UTC";
