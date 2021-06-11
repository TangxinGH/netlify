---
title: python3 thread not working  坑
date: 2021-03-30 19:58:31.000
updated: 2021-03-30 20:00:12.000
csdn_url: https://blog.csdn.net/weixin_43531940/article/details/115334348
description: 多线程不报错，
多进程不报错
A
B
C（A，B）
A,B写在上面
_thread （）函数线程，要使用，tuple 再加个逗号！！
 _thread.start_new_thread(sava_to_el, (data, job_id,))

而from concurrent.futures.thread import ThreadPoolExecutor  中
 pool.submit(sava_to_el, data, id)

不要tuple 。。。。。。。。。。。。不要括号民
不报错。。。。。


tags: python,多进程,tuple
categories: python
article_id: 115334348
---
﻿
多线程不报错，
多进程不报错

A
B
C（A，B）
A,B写在上面

_thread （）函数线程，要使用，tuple 再加个==逗号==！！

```python
 _thread.start_new_thread(sava_to_el, (data, job_id,))
```

而from concurrent.futures.thread import ThreadPoolExecutor  中
```python
 pool.submit(sava_to_el, data, id)
```
不要tuple 。。。。。。。。。。。。不要括号民
不报错。。。。。
