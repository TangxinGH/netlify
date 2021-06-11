---
title: unbutu字符集临时修改，ssh 终端斜杠中文
date: 2021-03-25 19:59:50.000
updated: 2021-03-25 20:01:37.000
csdn_url: https://blog.csdn.net/weixin_43531940/article/details/115217213
description: 输入：locale
输出
：
输入：查看你支持的字符集，
locale -a


输出了：
C
C.UTF-8
POSIX
修改
export LC_CTYPE=“en_US.utf8”
bash: warning: setlocale: LC_CTYPE: cannot change locale (en_US.utf8): No such file or directory
应该是这个再对。这个不用重启，临时的
export LC_CTYPE=“C.UTF-8”

...
tags: 乱码,ssh,linux字符设置
categories: Linux
article_id: 115217213
---
﻿
 输入：locale
 输出
 ：![在这里插入图片描述](http://img.yayi.site/csdn/2021032519591958.png-watermaskStyle)

 输入：查看你支持的字符集，
```bash
locale -a

```
输出了：


C
C.UTF-8
POSIX

修改
 export LC_CTYPE="en_US.utf8"
bash: warning: setlocale: LC_CTYPE: cannot change locale (en_US.utf8): No such file or directory

应该是这个再对。这个不用重启，临时的
 export LC_CTYPE="C.UTF-8"

