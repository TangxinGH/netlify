---
title: Linux根目录扩容 Gpart iso方式
date: 2020-06-11 18:31:18.000
updated: 2020-06-11 18:31:18.000
csdn_url: https://blog.csdn.net/weixin_43531940/article/details/106694393
description: 环境
centos7 vm虚拟机。我的是服务器版，非桌面
只有一个硬盘，vm扩展容量后。是末分配的。
要扩展的是sda3 主分区 根目录
开始
刚开始使用fdisk 好像说已分配的分区不能扩容。
然后使用 LVM 方法。好像vgscan 根本什么都 没有。按步骤来没用。可能是我不会用

听说Gpart不错，但我这不是GUI版的。然后安装了gnome startx; 是可以成功。但我不想装桌面。一般服务器都是没有GUI的。
然后，Gpart官方提供了一个iso镜像。我用虚拟机挂载后，再进入biso 启动顺序改
tags: Gpart,vm,centos7
categories: Linux
article_id: 106694393
---
﻿## 环境
centos7 vm虚拟机。我的是服务器版，非桌面

只有==一个硬盘==，vm扩展容量后。是末分配的。
要扩展的是sda3 主分区 根目录

## 开始
刚开始使用fdisk 好像说已分配的分区不能扩容。

然后使用 LVM 方法。好像vgscan 根本什么都 没有。按步骤来没用。可能是我不会用
![在这里插入图片描述](http://img.yayi.site/csdn/20200611182044464.png-watermaskStyle)

听说Gpart不错，但我这不是GUI版的。然后安装了gnome startx; 是可以成功。但我不想装桌面。一般服务器都是没有GUI的。

**然后，Gpart官方提供了一个iso镜像。我用虚拟机挂载后，再进入biso 启动顺序改为 这个CD 。然一路选择就行，好像可以有命令行模式和GUI模式选择。GUi模式下很容易就成功了。之后 移除CD** 
![在这里插入图片描述](http://img.yayi.site/csdn/20200611182629130.png-watermaskStyle)

==这种方法就不需要安装linux的gnome桌面。==

但服务器，一般也没有像vm虚拟机这样可以进biso的选项。或者插入硬件的方式。所以还是得通过命令行，不知道gpart有没有命令行版的。或者说，之前的LVM fdisk命令，应该可以吧，别人好像成功了。之后再看看吧，可能方法不对。。。

