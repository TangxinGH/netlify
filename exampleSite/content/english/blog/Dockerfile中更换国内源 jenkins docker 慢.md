---
title: Dockerfile中更换国内源 jenkins docker 慢
date: 2020-10-08 13:14:33.000
updated: 2020-10-08 13:14:33.000
csdn_url: https://blog.csdn.net/weixin_43531940/article/details/108962058
description: 场景：
  在docker中使用Dockerfile的方式进行构建自己的镜像时，发现构建的镜像默认使用国外的源，导致使用自己构造的镜像 启动容器后，在容器中安装软件慢的离谱，而且大多数情况下都会因为连接超时而失败，ubuntu中一个简单的vim都安装不了。

  那么，就想这在Dockerfile文件构建镜像的初期，就将新的镜像中的源给替换了。

操作步骤：
https://blog.csdn.net/yyj108317/article/details/105984674
方法二：
直接清华源：
搜索你镜像
tags: docker,dokcerfile,jenkinsDocker,慢
categories: 
article_id: 108962058
---
﻿场景：

      在docker中使用Dockerfile的方式进行构建自己的镜像时，发现构建的镜像默认使用国外的源，导致使用自己构造的镜像 启动容器后，在容器中安装软件慢的离谱，而且大多数情况下都会因为连接超时而失败，ubuntu中一个简单的vim都安装不了。

      那么，就想这在Dockerfile文件构建镜像的初期，就将新的镜像中的源给替换了。

操作步骤：
[https://blog.csdn.net/yyj108317/article/details/105984674](https://blog.csdn.net/yyj108317/article/details/105984674)

方法二：
直接清华源：
==搜索你镜像的系统的镜像源是怎么配置的==

或者直接云清华源搜索你的系统
我的是alipne
所以 https://mirrors.tuna.tsinghua.edu.cn/help/alpine/

在终端输入以下命令以替换TUNA镜像源：

sed -i 's/dl-cdn.alpinelinux.org/mirrors.tuna.tsinghua.edu.cn/g' /etc/apk/repositories
![在这里插入图片描述](http://img.yayi.site/csdn/20201008131013889.png-watermaskStyle)

简单

---
因为在jenkins中想重复使用docker images 不想每次构建，所以想搞个本地docker仓库（[教程](https://yeasy.gitbook.io/docker_practice/repository/registry)），好麻烦。
为什么不支持直接加载本地的镜像呢？？待续。知道怎么写jenkinsfile 的本地 docker images的告诉我一下。


