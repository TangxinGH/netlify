---
title: AS BottomNavigation does not have a NavController set
date: 2020-09-13 22:06:36.000
updated: 2020-09-13 22:06:36.000
csdn_url: https://blog.csdn.net/weixin_43531940/article/details/108569132
description: 使用AS 生成 activity  BottomNavigation
结果 ：does not have a NavController set
google stackoverflow
不行
重新生成 一个项目 as 生成BottomNav就能运行
于是把 启动activity 换为 Navigation
排查错误
https://www.cnblogs.com/zHQQQQ/p/12696995.html
我之前项目设置了NoactionBar
而且 setContentView 的布局 应该是

R8
tags: Navigation,ANDROID
categories: andriod
article_id: 108569132
---
﻿
### 使用AS 生成 activity  BottomNavigation
结果 ：==does not have a NavController set==

[google stackoverflow](https://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=&cad=rja&uact=8&ved=2ahUKEwiju62wpebrAhWXPXAKHWm5CtIQFjAAegQICxAB&url=https://stackoverflow.com/questions/50502269/illegalstateexception-link-does-not-have-a-navcontroller-set&usg=AOvVaw0sI_JbKbtRrzzed_tldnsb)

### 不行
重新生成 一个项目 as 生成BottomNav就能运行

### 于是把 启动activity 换为 Navigation 
排查错误 
[https://www.cnblogs.com/zHQQQQ/p/12696995.html](https://www.cnblogs.com/zHQQQQ/p/12696995.html)

###  我之前项目设置了NoactionBar 
而且 setContentView 的布局 应该是 
![在这里插入图片描述](http://img.yayi.site/csdn/20200913220402493.png-watermaskStyle)

R8:
![在这里插入图片描述](http://img.yayi.site/csdn/20200913220435706.png-watermaskStyle)
![在这里插入图片描述](http://img.yayi.site/csdn/20200913220525406.png-watermaskStyle)







[移除actionBar](https://stackoverflow.com/questions/50545521/removing-action-bar-in-bottomnavigation-view)
