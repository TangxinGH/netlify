---
title: android 下的判断网络是否连通的方法。
date: 2020-05-09 14:49:45.000
updated: 2020-05-09 14:49:45.000
csdn_url: https://blog.csdn.net/weixin_43531940/article/details/106018638
description: 参考文章



https://www.jianshu.com/p/1b542cece605

注意点

windows上和linux上的参数意义是不一样的
	安卓6以上用NetworkCapabilities 。6.00以下用经典方法。

Runtime runtime = Runtime.getRuntime();
                  try {
                    Process p = runtime.exec("ping -c 3 www.baidu.com".
tags: ping,安卓,网络连通
categories: andriod
article_id: 106018638
---
﻿
