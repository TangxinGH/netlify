---
title: Public Key Retrieval is not allowed
date: 2019-10-16 23:06:20.000
updated: 2019-10-16 23:06:20.000
csdn_url: https://blog.csdn.net/weixin_43531940/article/details/102596745
description: 很多种可能。
有一种是url问题
URI = “jdbc:mysql://localhost:3306/user?useSSL=false&amp;serverTimezone=UTC”;
传三个参数试试
DriverManager.getConnection(URI,USER,PASS);


tags: 
categories: javaweb
article_id: 102596745
---
﻿很多种可能。
有一种是url问题
URI = "jdbc:mysql://localhost:3306/user?useSSL=false&serverTimezone=UTC";
传三个参数试试
DriverManager.getConnection(URI,USER,PASS);
