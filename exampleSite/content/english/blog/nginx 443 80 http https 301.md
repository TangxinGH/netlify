---
title: nginx 443 80 http https 301
date: 2021-03-20 17:35:19.000
updated: 2021-03-20 17:35:58.000
csdn_url: https://blog.csdn.net/weixin_43531940/article/details/115031549
description: 利用重定向来全部443
要www 还是不要的好。不知道，听说www不要的话，一些网站有些问题
301重定向永久之后，通过F12》disable cache禁用缓存来解决，否则浏览器会缓存301到本地，导致更新不起作用，google chrome 是这样的。

...
tags: nginx,缓存,301,浏览器,https
categories: 网络
article_id: 115031549
---
﻿利用重定向来全部443
要www 还是不要的好。不知道，听说www不要的话，一些网站有些问题

301重定向永久之后，通过F12》disable cache禁用缓存来解决，否则浏览器会缓存301到本地，导致更新不起作用，google chrome 是这样的。
