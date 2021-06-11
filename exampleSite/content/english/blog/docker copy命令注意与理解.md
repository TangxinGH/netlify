---
title: docker copy命令注意与理解
date: 2021-04-30 15:40:54.000
updated: 2021-04-30 15:41:57.000
csdn_url: https://blog.csdn.net/weixin_43531940/article/details/116304740
description: copy dir1 ./
结果并不是
./
dir1
而是
./
dir1里的文件与目录

第二
COPY dir1/*  ./
结果并不是
./
dir1
xxx/file.txt
而是
./
file.txt
也就是dir1的目录结构不会复制。*号是将所有目录/包括子目录下的文件复制而已


...
tags: python,docker compose
categories: Linux,python
article_id: 116304740
---
﻿copy dir1 ./

结果并不是
./
    dir1

而是
./ 
    dir1里的文件与目录



---
第二

COPY dir1/*  ./ 

结果并不是
./   
   dir1
          xxx/file.txt

而是
./
   file.txt

也就是dir1的目录结构不会复制。*号是将所有目录/包括子目录下的文件复制而已

---


