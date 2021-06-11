---
title: thinkphp日志
date: 2019-11-16 09:40:08.000
updated: 2019-11-16 09:40:08.000
csdn_url: https://blog.csdn.net/weixin_43531940/article/details/103095299
description: https://www.cnblogs.com/xu1115/p/11118664.html
博客园 首页 新随笔 联系 管理 订阅订阅 随笔- 58  文章- 0  评论- 0
thinkPHP5 日志的写入
版本	新增功能
5.0.16	增加文件日志自动清理功能支持
5.0.13	增加单文件日志写入功能
5.0.10	增加record_trace配置参数用于记录trace信息到日志
5.0.4...
tags: 
categories: php
article_id: 103095299
---
﻿首先你要导入这个日志类，否则类找不到
然后看开发手册
日志还要给权限
linux mkdir(): Permission denied
[http://www.thinkphp.cn/topic/42633.html](http://www.thinkphp.cn/topic/42633.html)
我的是控制器里写文件，我直接给了application 777权限
runtime 777

具体情况，输出路径看看，运行者权限。。。
