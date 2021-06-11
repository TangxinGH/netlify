---
title: linux学习记录，
date: 2019-12-05 18:31:35.000
updated: 2019-12-05 18:31:35.000
csdn_url: https://blog.csdn.net/weixin_43531940/article/details/103404831
description: HTTPPIE
CURL
esc 退出编辑，：q退出
could not retrieve mirrorlist http://
https://blog.csdn.net/qq_33733970/article/details/81200980
cd etc/sysconfig/network-scripts/
ls
找到ifcfg-你的网卡名
onboot=on
reboot
清屏clear
...
tags: linux,vmtools,man,yum,yum镜像
categories: Linux
article_id: 103404831
---
﻿HTTPPIE
CURL
esc 退出编辑，：q退出
could not retrieve mirrorlist http://
[https://blog.csdn.net/qq_33733970/article/details/81200980](https://blog.csdn.net/qq_33733970/article/details/81200980)
cd etc/sysconfig/network-scripts/
ls
找到ifcfg-你的网卡名
onboot=on
reboot
清屏clear
查看ip 
ip addr
ssh:先桥接，后，vm -> 连接到ssh
ssh 好处：可以用第三方工具复制粘贴，vm linux下无法ctrl v

### post提交上网，curl -d "data "  "202.193.80.124"
wget -post-data=""
ping:
卡死，没反应 ctrL +c

win10自带ssh
https://blog.csdn.net/sherjf/article/details/86797745

复制方式putty https://www.cnblogs.com/softidea/p/6388357.html
https://blog.csdn.net/ablo_zhou/article/details/3794373


vmtools可以命令行安装

vmtoos 共享文件夹  linux 在mnt/hgfsl/中

---
镜像加速:在清华镜像的下面帮助那里
![在这里插入图片描述](http://img.yayi.site/csdn/20200505190941379.png-watermaskStyle)

：[https://mirrors.tuna.tsinghua.edu.cn/](https://mirrors.tuna.tsinghua.edu.cn/)直接访问镜像站，官网有安装配置方法，因为一些博客的方法会过时。



---
代理：
yum 设置代理上网，编辑 /etc/yum.conf ，
系统全局代理：-->测试可用
　　　　　　编辑 /etc/profile ,追加如下内容：
　　　　　　
[https://www.jianshu.com/p/89f7ff080c0a](https://www.jianshu.com/p/89f7ff080c0a)
[https://mirror.tuna.tsinghua.edu.cn/help/centos/](https://mirror.tuna.tsinghua.edu.cn/help/centos/)
或者用软件

如果只是暂时使用代理,在命令行输入下面一条命令:

export http_proxy="http://210.45.72.XX:808"

---
快捷：如果你不记得命令怎么用，man 加命令可以查看用法，或者命令加 -h试试
