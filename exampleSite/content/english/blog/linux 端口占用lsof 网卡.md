---
title: linux 端口占用lsof 网卡
date: 2020-05-16 18:20:43.000
updated: 2020-05-16 18:20:43.000
csdn_url: https://blog.csdn.net/weixin_43531940/article/details/106121579
description: lsof -i:端口号
list open file


tags: vm docker,网卡,端口占用
categories: 
article_id: 106121579
---
﻿lsof -i:端口号
list open file
神奇的方法

vm 虚拟机安装docker 后，vm ssh 连上了docker 的网卡。
方法：删除vm的网络适配器网卡，再新添加就可以了



