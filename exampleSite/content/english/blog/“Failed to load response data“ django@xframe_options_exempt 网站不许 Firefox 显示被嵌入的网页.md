---
title: “Failed to load response data“ django@xframe_options_exempt 网站不许 Firefox 显示被嵌入的网页
date: 2021-04-06 17:48:00.000
updated: 2021-04-06 17:50:03.000
csdn_url: https://blog.csdn.net/weixin_43531940/article/details/115466566
description: python django ajax
chrome 显示 failed to xxx 。以为ajax 数据量大。


设置ajax 的timeout 没有用


换firefox 网站不许 Firefox 显示被嵌入的网页 。哦。（firefox nb）


django 的官方 xframe_options_exempt 在view的视图方法上注解





ok.安全问题。



...
tags: ajax,django,firefox 嵌入网页
categories: python
article_id: 115466566
---
﻿# python django ajax

chrome 显示 failed to xxx 。以为ajax 数据量大。

1. 设置ajax 的timeout 没有用
2. 换firefox 网站不许 Firefox 显示被嵌入的网页 。哦。（firefox nb）
3. django 的官方 xframe_options_exempt [在view的视图方法上注解](https://docs.djangoproject.com/en/3.1/ref/clickjacking/)
4. ![在这里插入图片描述](http://img.yayi.site/csdn/20210406174917938.png-watermaskStyle)

5. ok.安全问题。

