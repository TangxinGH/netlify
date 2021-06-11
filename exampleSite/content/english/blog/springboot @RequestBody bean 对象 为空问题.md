---
title: springboot @RequestBody bean 对象 为空问题
date: 2020-10-11 19:19:24.000
updated: 2020-10-11 19:19:24.000
csdn_url: https://blog.csdn.net/weixin_43531940/article/details/109015203
description: 确认 数据是传入
f12  。
fiddler
debug
改为字符串接收
确认了是接收到了。


关键是spring没有报错
spring 内置jackjson
startweb 中。


debug进源码 ，新的世界


打开 spring debug 级别输出
确实有东西收到了。
是转换的时候出问题


实在 不行用第三方的手动转。
加了pom jackjson依赖，



这下有有错了：
Unrecognized field , not marked as ignorable
百度一下。

ja..
tags: spring,RequestBody
categories: # springboot
article_id: 109015203
---
﻿1. 确认 数据是传入
  f12  。
  fiddler
  debug 
  改为字符串接收
  确认了是接收到了。
2. 关键是spring没有报错
 spring 内置jackjson
 startweb 中。


3. debug进源码 ，新的世界
  
4. 打开 spring debug 级别输出 
  确实有东西收到了。
  是转换的时候出问题
5. 实在 不行用第三方的手动转。
  加了pom jackjson依赖，
---
这下有有错了：
Unrecognized field , not marked as ignorable
百度一下。


---

javabean 有个规范的。


[json字符转java bean忽略大小写](https://www.shuzhiduo.com/A/D854DloV5E/)

---

spring boot json 首字母大小写问题解决方案
　　 spring boot默认使用的json解析框架是jackson，对于.net转java的项目来说太坑了，首字母大写的属性会自动转为小写，然后前端就悲剧了，十几个属性的ViewModel增加几个JsonField注解能解决问题，但若有几十上百个属性，那就只能换json框架了，幸好有fastjson能原样输出属性，下面是spring boot 使用fastjson的实施步骤，原文来自https://blog.csdn.net/cjq2013/article/details/76421101。

---

[springboot bug实例8 ：javaBean的规范导致json传参首字母大写将永远获取不到](https://www.jianshu.com/p/fe54ecf90742)

　　 

---
为什么spring 不报错，也不警告？
debug 下不应该是日志算高了吧。难道要all

要不配置一一下：
[https://blog.csdn.net/qq_40741855/article/details/104838898](https://blog.csdn.net/qq_40741855/article/details/104838898)

application.yaml 配置

----
[json规范](https://github.com/darcyliu/google-styleguide/blob/master/JSONStyleGuide.md)
