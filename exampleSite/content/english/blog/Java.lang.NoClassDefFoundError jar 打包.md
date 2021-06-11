---
title: Java.lang.NoClassDefFoundError jar 打包
date: 2020-07-30 19:42:36.000
updated: 2020-07-30 19:42:36.000
csdn_url: https://blog.csdn.net/weixin_43531940/article/details/107698451
description: 更改过pom文件后，运行是没问题，打包jar就Java.lang.NoClassDefFoundError

右边的输出到左边。

发现jar文件目录中并没有 http 这个包。
androidstudio４．０也有这个问题，一般清除缓存，重新编译就行？

...
tags: ｄｅｆｆｏｕｎｄＥｒｒｏｒ,java
categories: java
article_id: 107698451
---
﻿### 更改过pom文件后，运行是没问题，打包jar就Java.lang.NoClassDefFoundError
ＩＤＥＡ 当时从当时依赖建立的artifacts ，所以依赖改变后artifacts配置并没有更新。所以出来的jar 中没有类，发现jar文件目录中并没有 http 这个包。。java -jar时有问题。IDE时没有问题。
方法一：
![在这里插入图片描述](http://img.yayi.site/csdn/20200730193846908.png-watermaskStyle)
右边的输出到左边。![在这里插入图片描述](http://img.yayi.site/csdn/20200730194038703.png-watermaskStyle)
![在这里插入图片描述](http://img.yayi.site/csdn/20200730194100989.png-watermaskStyle)
方法二：
重新建一个artifacts。
方法三：

androidstudio４．０也有这个问题，一般清除缓存，重新编译就行？

### 如何删掉jar中多余的东西。
方法一：如何你是 自己导的jar 直接修改jar. 
方法二：maven的。复制一份包。 自己修改包，然后在项目配置中当作库引入。在输出jar是artifacts中output root就行。
