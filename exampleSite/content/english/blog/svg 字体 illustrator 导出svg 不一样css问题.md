---
title: svg 字体 illustrator 导出svg 不一样css问题
date: 2021-04-17 13:12:25.000
updated: 2021-04-17 13:12:25.000
csdn_url: https://blog.csdn.net/weixin_43531940/article/details/115793623
description: illustrator 导出svg，用的是同一字体 ，导出到网页，不一样。
原来是原本css文件中中加了serif;line-height: 1.8;等。加上就可以了


tags: 
categories: 前端
article_id: 115793623
---
﻿illustrator 导出svg，用的是同一字体 ，导出到网页，不一样。

原来是原本css文件中中加了serif;line-height: 1.8;等。加上就可以了

我的加font-family没有用。

因此直接写svg标签在html里，而不是img 引入方式。解决字体问题。

后来发现，字体颜色不对。fill="#233300" 来修改颜色。

默认bold加粗

 
