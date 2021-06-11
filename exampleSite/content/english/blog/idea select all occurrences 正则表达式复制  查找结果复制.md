---
title: idea select all occurrences 正则表达式复制  查找结果复制
date: 2020-11-26 12:46:20.000
updated: 2020-11-26 12:46:20.000
csdn_url: https://blog.csdn.net/weixin_43531940/article/details/110183275
description: 一些场景下复制东西
正则表达式选出所有的 color 进行复制 R.color.pink
变成这样：


源码：
  addItem("John", new String[]{"House", "Boat", "Candy", "Collection", "Sport", "Ball", "Head"}, R.color.pink, R.drawable.ic_ghost);
        addItem("Mary", new String[]{"Dog", "Horse", "Boat"}, R.co
tags: 正则表达式
categories: IDE
article_id: 110183275
---
﻿一些场景下复制东西

 正则表达式选出所有的 color 进行复制 R.color.pink
变成这样：
![在这里插入图片描述](http://img.yayi.site/csdn/20201126124507533.png-watermaskStyle)


----

源码：

```kotlin
  addItem("John", new String[]{"House", "Boat", "Candy", "Collection", "Sport", "Ball", "Head"}, R.color.pink, R.drawable.ic_ghost);
        addItem("Mary", new String[]{"Dog", "Horse", "Boat"}, R.color.blue, R.drawable.ic_ghost);
        addItem("Ana", new String[]{"Cat"}, R.color.purple, R.drawable.ic_ghost);
        addItem("Peter", new String[]{"Parrot", "Elephant", "Coffee"}, R.color.yellow, R.drawable.ic_ghost);
        addItem("Joseph", new String[]{}, R.color.orange, R.drawable.ic_ghost);
        addItem("Paul", new String[]{"Golf", "Football"}, R.color.green, R.drawable.ic_ghost);
        addItem("Larry", new String[]{"Ferrari", "Mazda", "Honda", "Toyota", "Fiat"}, R.color.blue, R.drawable.ic_ghost);
        addItem("Moe", new String[]{"Beans", "Rice", "Meat"}, R.color.yellow, R.drawable.ic_ghost);
        addItem("Bart", new String[]{"Hamburger", "Ice cream", "Candy"}, R.color.purple, R.drawable.ic_ghost);
```
![在这里插入图片描述](http://img.yayi.site/csdn/2020112612440217.png-watermaskStyle)
![在这里插入图片描述](http://img.yayi.site/csdn/20201126124416603.png-watermaskStyle)
然后ctrl c 即可 


