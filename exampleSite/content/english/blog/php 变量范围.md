---
title: php 变量范围
date: 2020-06-02 14:48:18.000
updated: 2020-06-02 14:48:18.000
csdn_url: https://blog.csdn.net/weixin_43531940/article/details/106495961
description: 参考官方文档：
https://www.php.net/manual/zh/language.variables.scope.php
&lt;?php
$a = 1; /* global scope */

function Test()
{
    echo $a; /* reference to local scope variable */
}

Test();
?&gt;


这个脚本不会有任何输出，因为 echo 语句引用了一个局部版本的变量 $a，而且在这个范围内，它并没有被赋值。你可能注意到 
tags: php
categories: php
article_id: 106495961
---
﻿参考官方文档：
[https://www.php.net/manual/zh/language.variables.scope.php](https://www.php.net/manual/zh/language.variables.scope.php)

```php
<?php
$a = 1; /* global scope */

function Test()
{
    echo $a; /* reference to local scope variable */
}

Test();
?>
```

![在这里插入图片描述](http://img.yayi.site/csdn/20200602144526997.png-watermaskStyle)
这个脚本不会有任何输出，因为 echo 语句引用了一个局部版本的变量 $a，而且在这个范围内，它并没有被赋值。你可能注意到 PHP 的全局变量和 C 语言有一点点不同，在 C 语言中，全局变量在函数中自动生效，除非被局部变量覆盖。这可能引起一些问题，有些人可能不小心就改变了一个全局变量。PHP 中全局变量在函数中使用时必须声明为 global。

```php
<?php
$a = 1;
$b = 2;

function Sum()
{
    global $a, $b;

    $b = $a + $b;
}

Sum();
echo $b;
?>
```

