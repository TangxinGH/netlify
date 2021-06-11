---
title: tinymce is not a valid module  layui is not define
date: 2019-11-11 13:19:16.000
updated: 2019-11-11 13:19:35.000
csdn_url: https://blog.csdn.net/weixin_43531940/article/details/103008510
description: 路径问题

不管是 …/ 还是./
我这里都不会404， 但偏偏就是undefine…



tags: 
categories: 前端
article_id: 103008510
---
﻿路径问题
![在这里插入图片描述](http://img.yayi.site/csdn/2019111113180333.png-watermaskStyle)
不管是 ../ 还是./
我这里都不会404， 但偏偏就是undefine.....

![在这里插入图片描述](http://img.yayi.site/csdn/20191111131917569.png-watermaskStyle)



idea 到tomcat 的部署

因为我的idea是9090根目录没有Demo项目名
所以存在一些./和/的区别 ，404，太多无法解决

所以干脆将，tomcat的ROOT 改为我的，

要改的话就在这里webapps/root/里面文件改，不然idea的 可能也会404，而且，不需要idea编译打包，再复制，再开tomcat这样麻烦。-

对比副本webapps就知道区别了。


直接将demo 中的target 下的项目复制到你tomcat下就行了。不需要建立war包
