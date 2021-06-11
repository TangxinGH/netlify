---
title: date.getMonth()  date.getDate())
date: 2020-11-01 13:16:08.000
updated: 2020-11-01 13:16:08.000
csdn_url: https://blog.csdn.net/weixin_43531940/article/details/109422761
description: Date date = new Date();
System.out.println(date.getMonth());
System.out.println(date.getDate());
这个已经弃用了
使用
Returns a number representing the month that contains or begins with the instant in time represented by this Date object. The value returned is betw
tags: java,getMonth,getDate
categories: java
article_id: 109422761
---
﻿ Date date = new Date();
        System.out.println(date.getMonth());
        System.out.println(date.getDate());
这个已经弃用了
使用
```java
Returns a number representing the month that contains or begins with the instant in time represented by this Date object. The value returned is between 0 and 11, with the value 0 representing January.
Deprecated
As of JDK version 1.1, replaced by Calendar.get(Calendar.MONTH).
Returns:
the month represented by this date.
```

但面试题喜欢考。。。。

getMonth 返回0到11 分别 代码 1-12 月。
date.getDate() 返回日期：
```java
Returns the day of the month represented by this Date object. The value returned is between 1 and 31 representing the day of the month that contains or begins with the instant in time represented by this Date object, as interpreted in the local time zone.
Deprecated
As of JDK version 1.1, replaced by Calendar.get(Calendar.DAY_OF_MONTH).
Returns:
the day of the month represented by this date.

```

==还有一个问题== 
、System.out.println   能重定向到别的输出流，这样的话你在屏幕上将看不到打印的东西了，  
 System.err.println    只能在屏幕上实现打印，即使你重定向了也一样。

 JVM和操作系统的组合体并不会立即输出这个流。相反，它将保持等待状态直到将要输出的东西达到一定的量。 
2、当向控制台输出信息时，开发者有两个选择：System.out和System.err。使用者更倾向于输出的是System.out，而如果是 System.err则输出“error”。尽管这看起来是显而易见的，但很多开发者都不了解为什么出错和调试时使用System.err。（如果你使用err打印出的字符串，在eclipse的console会显示成红色的哦。)
