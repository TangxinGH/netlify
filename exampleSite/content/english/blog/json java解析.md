---
title: json java解析
date: 2019-11-13 13:52:21.000
updated: 2019-11-13 13:54:41.000
csdn_url: https://blog.csdn.net/weixin_43531940/article/details/103047955
description: fastjson
因为json中即有对象也有数组
{imgurl:xxx, [{}]}
 JSONObject json = JSON.parseObject(jsonStr);
     String  newslist = json.getString("newslist");//因为对象中有数组
    JSONArray jsonArr = JSON.parseArray(newslist...
tags: 
categories: javaweb
article_id: 103047955
---
﻿fastjson
因为json中即有对象也有数组
{imgurl:xxx, [{}]}

```java
 JSONObject json = JSON.parseObject(jsonStr);
     String  newslist = json.getString("newslist");//因为对象中有数组
    JSONArray jsonArr = JSON.parseArray(newslist);//数组中再取

    String first = jsonArr.get(0).toString();// 第一个  原因是：改提取出来的对象不能转为String，而要通过它的方法 toString 来转化：
    JSONObject imgurljson = JSON.parseObject(first);
    String imgurl = imgurljson.getString("imgurl");
    String date=json.getString("date");
```
多转一次就行，取对象中newslist转数组，再转jsonstring,再取值

