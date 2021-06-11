---
title: centos8 虚拟机ip问题
date: 2020-05-17 22:15:08.000
updated: 2020-05-17 22:15:08.000
csdn_url: https://blog.csdn.net/weixin_43531940/article/details/106182236
description: nmcli c up ens33 第次要激活
每次打开虚拟机，用XShell连接前，都要输入ifup eth0,特别烦。
解决方法:
修改ifcfg-eth0中 ONBOOT属性为yes
ifcfg-eth0 一般在 /etc/sysconfig/network-scripts
https://blog.csdn.net/SZStudy/article/details/79439032

https://www.jb51.net/article/173041.htm
vmtools 灰色 不要删除那些 C.
tags: vmware,vmtools灰色
categories: Linux
article_id: 106182236
---
﻿![file](http://img.yayi.site/csdn/aHR0cHM6Ly9ncmFwaC5iYWlkdS5jb20vcmVzb3VyY2UvMjIyNGRlMGMzMTliOWU2ZjZkMDIxMDE1ODk3MTk2MTcucG5n-watermaskStyle)

 nmcli c up ens33 第次要激活
 
 每次打开虚拟机，用XShell连接前，都要输入ifup eth0,特别烦。

解决方法:

修改ifcfg-eth0中 ONBOOT属性为yes

ifcfg-eth0 一般在 /etc/sysconfig/network-scripts

[https://blog.csdn.net/SZStudy/article/details/79439032](https://blog.csdn.net/SZStudy/article/details/79439032)


![file](http://img.yayi.site/csdn/aHR0cHM6Ly9ncmFwaC5iYWlkdS5jb20vcmVzb3VyY2UvMjIyZjAwZjRiZGFhZDBmZWMyOTI1MDE1ODk3MTk4MTUucG5n-watermaskStyle)

https://www.jb51.net/article/173041.htm


vmtools 灰色 不要删除那些 CD盘 改为自动检测 。md 好像不行。centos 8  删除其实cd盘，留一个就行和一个软盘。cd 加载linux.iso文件。
原因：[https://madder.blog.idealisan.com/2020/01/05/%E6%A0%B9%E6%9C%AC%E4%B8%8A%E8%A7%A3%E5%86%B3vmware%E7%9A%84%E9%87%8D%E6%96%B0%E5%AE%89%E8%A3%85vmware-tools%E6%98%AF%E7%81%B0%E8%89%B2%E7%9A%84/]https://madder.blog.idealisan.com/2020/01/05/%E6%A0%B9%E6%9C%AC%E4%B8%8A%E8%A7%A3%E5%86%B3vmware%E7%9A%84%E9%87%8D%E6%96%B0%E5%AE%89%E8%A3%85vmware-tools%E6%98%AF%E7%81%B0%E8%89%B2%E7%9A%84/()


linux目录/dev

设备文件一般存放在/dev目录下，对常见设备文件作如下说明：
```c
　　/dev/hd[a-t]：IDE设备

　　/dev/sd[a-z]：SCSI设备

　　/dev/fd[0-7]：标准软驱

　　/dev/md[0-31]：软raid设备

　　/dev/loop[0-7]：本地回环设备

　　/dev/ram[0-15]：内存

　　/dev/null：无限数据接收设备,相当于黑洞

　　/dev/zero：无限零资源

　　/dev/tty[0-63]：虚拟终端

　　/dev/ttyS[0-3]：串口

　　/dev/lp[0-3]：并口

　　/dev/console：控制台

　　/dev/fb[0-31]：framebuffer

　　/dev/cdrom => /dev/hdc

　　/dev/modem => /dev/ttyS[0-9]

　　/dev/pilot => /dev/ttyS[0-9]

　　/dev/random：随机数设备

　　/dev/urandom：随机数设备
	
	```c
————————————————
版权声明：本文为CSDN博主「maopig」的原创文章，遵循CC 4.0 BY-SA版权协议，转载请附上原文出处链接及本声明。
原文链接：https://blog.csdn.net/maopig/article/details/7195048

https://docs.vmware.com/cn/VMware-Workstation-Pro/15.0/com.vmware.ws.using.doc/GUID-08BB9465-D40A-4E16-9E15-8C016CC8166F.html
