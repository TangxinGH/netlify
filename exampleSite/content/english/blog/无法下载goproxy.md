---
title: 无法下载goproxy
date: 2019-10-25 20:59:27.000
updated: 2019-10-26 21:22:59.000
csdn_url: https://blog.csdn.net/weixin_43531940/article/details/102749897
description: 手动安装
#!/bin/bash
F=“proxy-admin_linux-amd64.tar.gz”
cd /tmp
rm -rf FLASTVERSION=F
LAST_VERSION=FLASTV​ERSION=(curl --silent “https://api.github.com/repos/snail007/proxy_admin_free/releases/latest” | g...
tags: 
categories: Linux
article_id: 102749897
---
﻿手动安装
#!/bin/bash
F="proxy-admin_linux-amd64.tar.gz"
cd /tmp
rm -rf $F
LAST_VERSION=$(curl --silent "https://api.github.com/repos/snail007/proxy_admin_free/releases/latest" | grep -Po '"tag_name": "\K.*?(?=")')
wget "https://github.com/snail007/proxy_admin_free/releases/download/${LAST_VERSION}/$F"

# #install
tar zxvf $F
chmod +x proxy-admin
./proxy-admin uninstall >/dev/null 2>&1 
./proxy-admin install
rm $F
systemctl  status proxyadmin &
sleep 1
echo "install done, please visit : http://YOUR_IP:32080/"
