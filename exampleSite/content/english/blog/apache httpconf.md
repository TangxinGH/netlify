---
title: apache httpconf
date: 2019-10-21 20:06:36.000
updated: 2019-10-21 20:06:59.000
csdn_url: https://blog.csdn.net/weixin_43531940/article/details/102670826
description: 对这个文件的改动（备份好），都要重启apache生效.
里面有错误是不能启动的，不能启动时。一条条加，判断是你修改了哪个配置的问题，也有可能是路径问题。可以在log文件查看日志，cmd下启动可能会有提示httpd.exe -k start
httpd.exe -k restart
httpd  -k install

...
tags: 
categories: 网络
article_id: 102670826
---
﻿对这个文件的改动（备份好），都要重启apache生效.
里面有错误是不能启动的，不能启动时。一条条加，判断是你修改了哪个配置的问题，也有可能是路径问题。可以在log文件查看日志，cmd下启动可能会有提示httpd.exe -k start
httpd.exe -k restart
httpd  -k install
