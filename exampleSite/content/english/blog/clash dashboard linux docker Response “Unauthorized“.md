---
title: clash dashboard linux docker Response “Unauthorized“ 
date: 2021-03-23 19:34:49.000
updated: 2021-03-23 19:44:34.000
csdn_url: https://blog.csdn.net/weixin_43531940/article/details/115139023
description: Response "Unauthorized" · Issue #692 · kubernetes/dashboard (github.com)

先用ip来试先

先把 docker prune 清一遍先，挂载的备份一下

先CNAME 的改为ip先，不要域名。

外部访问的设置密码，config.yaml

Response "Unauthorized" 的访问ip:port/ui 试试，然后去设置哪里改一下，设置外部控制器，ip port secert

总之对应就行了。

之后 ，再搞域...
tags: docker,ssh,clash dashboard
categories: Linux
article_id: 115139023
---
﻿
