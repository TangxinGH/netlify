---
title: ubuntu网络图标不见
date: 2019-11-22 21:48:26.000
updated: 2019-11-22 21:48:26.000
csdn_url: https://blog.csdn.net/weixin_43531940/article/details/103207909
description: service NetworkManager stop
yayi@ubuntu:~$ sudo service network-manager stop
[sudo] yayi 的密码： 
yayi@ubuntu:~$ sudo rm /var/lib/NetworkManager/NetworkManager.state
yayi@ubuntu:~$ sudo service network-m...
tags: 
categories: Linux
article_id: 103207909
---
﻿```css
service NetworkManager stop
yayi@ubuntu:~$ sudo service network-manager stop
[sudo] yayi 的密码： 
yayi@ubuntu:~$ sudo rm /var/lib/NetworkManager/NetworkManager.state
yayi@ubuntu:~$ sudo service network-manager start
yayi@ubuntu:~$ 


```

