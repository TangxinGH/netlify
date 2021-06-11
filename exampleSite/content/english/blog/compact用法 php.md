---
title: compact用法 php
date: 2020-06-02 14:58:34.000
updated: 2020-06-02 14:58:34.000
csdn_url: https://blog.csdn.net/weixin_43531940/article/details/106496293
description: 对每个参数，compact() 在当前的符号表中查找该变量名并将它添加到输出的数组中，变量名成为键名而变量的内容成为该键的值。简单说，它做的事和 extract() 正好相反。返回将所有变量添加进去后的数组。
错误的用法：
$b ='ds';
$c ='f';
$d=compact($a,$b,$c);
print_r($d);

正确方法见官方文档：
$b ='ds';
$c ='f';
$d=compact('b','c','a');
print_r($d);

传的真的是’名‘。
把一个或多个变量，建
tags: php
categories: php
article_id: 106496293
---
﻿对每个参数，compact() 在当前的符号表中查找该变量名并将它添加到输出的数组中，变量名成为键名而变量的内容成为该键的值。简单说，它做的事和 extract() 正好相反。返回将所有变量添加进去后的数组。
错误的用法：
```php
$b ='ds';
$c ='f';
$d=compact($a,$b,$c);
print_r($d);
```

正确方法见官方文档：

```php
$b ='ds';
$c ='f';
$d=compact('b','c','a');
print_r($d);
```
传的真的是’名‘。
把一个或多个变量，建立成数组元素，这些数组元素的键名就是变量的变量名，值是变量的值

