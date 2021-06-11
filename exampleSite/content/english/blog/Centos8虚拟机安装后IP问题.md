---
title: Centos8虚拟机安装后IP问题
date: 2020-05-17 20:30:50.000
updated: 2020-05-17 20:30:50.000
csdn_url: https://blog.csdn.net/weixin_43531940/article/details/106180179
description: 忘记截图了。
https://www.jb51.net/article/173041.htm
方法：激活网卡的3种方式（相当于ifup）：
（1）# nmcli c up ens33
就可以了
一、CentOS 7和CentOS 8网络配置区别：
VMware Workstation 15 Pro中安装了CentOS 8.0.1905，但在配置IP地址过程中发现没有了network.service，并且/etc/sysconfig/network-scripts目录中也没有任何脚本文件，CentOS 7中同
tags: linux,vmare ip
categories: Linux
article_id: 106180179
---
﻿忘记截图了。

[https://www.jb51.net/article/173041.htm](https://www.jb51.net/article/173041.htm)


方法：激活网卡的3种方式（相当于ifup）：

（1）# nmcli c up ens33


就可以了
一、CentOS 7和CentOS 8网络配置区别：

VMware Workstation 15 Pro中安装了CentOS 8.0.1905，但在配置IP地址过程中发现没有了network.service，并且/etc/sysconfig/network-scripts目录中也没有任何脚本文件，CentOS 7中同时支持network.service和NetworkManager.service（简称NM）2种方式配置网络，而在CentOS 8中已经废弃network.service，必须通过NetworkManager.service配置网络。


还是不要尝新的好
