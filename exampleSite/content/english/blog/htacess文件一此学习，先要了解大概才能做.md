---
title: .htacess文件一此学习，先要了解大概才能做
date: 2020-06-17 15:35:02.000
updated: 2020-06-17 15:35:02.000
csdn_url: https://blog.csdn.net/weixin_43531940/article/details/106809471
description: 文件.htaccess
重定向方法
重定向方法：
#两个方法
#RewriteEngine On
#RewriteRule ^/ http://localhost:8080/blog [R=301,L]
二：
&lt;Files ~ “^.(htaccess|htpasswd)$”&gt;
deny from all

Redirect permanent http://localhost:8080/ http://localhost:8080/blog
order deny,allow
首先要开启：
ht
tags: .htacesss
categories: 网络
article_id: 106809471
---
﻿## 文件.htaccess

### 重定向方法



重定向方法：

#两个方法
#RewriteEngine On
#RewriteRule ^/ http://localhost:8080/blog [R=301,L]

二：

<Files ~ "^\.(htaccess|htpasswd)$">
deny from all
</Files>
Redirect permanent http://localhost:8080/ http://localhost:8080/blog
order deny,allow

### 首先要开启：

https://blog.csdn.net/wujiangwei567/article/details/40627143?utm_medium=distribute.pc_relevant_t0.none-task-blog-BlogCommendFromMachineLearnPai2-1.nonecase&depth_1-utm_source=distribute.pc_relevant_t0.none-task-blog-BlogCommendFromMachineLearnPai2-1.nonecase

### 一些工具

在线编辑工具：

http://www.htaccesseditor.com/sc.shtml#a_redirect

[外链图片转存失败,源站可能有防盗链机制,建议将图片保存下来直接上传(img-c3e4B3Fg-1592379219274)(https://img.vim-cn.com/31/94f34451659b14f01c788ad57497940ac88630.png)]





### 一些功能 

比如防盗链：

https://blog.csdn.net/u012717614/article/details/56485129




