---
title: PHP调试-环境选择-window 原理principle调试流程解析 DBGp是什么 cmd乱码
date: 2021-01-01 14:00:27.000
updated: 2021-01-01 14:00:27.000
csdn_url: https://blog.csdn.net/weixin_43531940/article/details/112060026
description: PHP调试-环境选择-window
应该要了解一下原理，而不是配。
还有这文章写于2021.1.1。如果过时了就不要照着复制粘贴了。
这里只是记录一下原理。不是教程。
官网的写的非常好了
https://www.jetbrains.com/zh-cn/phpstorm/documentation/debugging/

这篇文章流程解析写的好：
https://learnku.com/articles/4090/the-first-step-to-becoming-a-senior-php-programm
tags: phpstorm调试,xdebug调试,cmd乱码,调试原理,调试流程
categories: IDE,php
article_id: 112060026
---
﻿
# PHP调试-环境选择-window 

应该要了解一下原理，而不是配。

还有这文章写于2021.1.1。如果过时了就不要照着复制粘贴了。
这里只是==记录一下原理。不是教程。 只是整理教程记录链接！==

官网的写的非常好了

https://www.jetbrains.com/zh-cn/phpstorm/documentation/debugging/

![image-20210101114112374](http://img.yayi.site/csdn/f1ee1b928024dee20a319f4d0fb9d22e.png-watermaskStyle)



这篇文章流程解析写的好：

https://learnku.com/articles/4090/the-first-step-to-becoming-a-senior-php-programmer-debugging-xdebug-principle



调试真是绝望

环境:window + phpstorm+php7

xdebug 和zend 两种工具只能二选一，会有冲突。

我选xdebug

调试均分为远程和本地两种

先引用一张动态原理图：

![dd](http://img.yayi.site/csdn/b41abaff54aba56b16803dee72f52335.gif-watermaskStyle)

![模式二](http://img.yayi.site/csdn/715981dfa2768e30b17fe7829ff3fe4a.gif-watermaskStyle)

### 本地

#### 脚本类调试

参考：https://www.jetbrains.com/help/phpstorm/debugging-a-php-cli-script.html

我使用的是xdebug 调试

- [ ] ctrl alt s 配置一下解释器

  ![image-20210101103600476](http://img.yayi.site/csdn/e7da64885982d33e6d091fb33b5a3073.png-watermaskStyle)

- [ ] 配置一下php.ini 。参考xdebug 安装，安装完成后会显示调试器就算成功，重启 php .exe 运行成功不报错, 配置就没问题。[外链图片转存失败,源站可能有防盗链机制,建议将图片保存下来直接上传(img-rI8ZNiem-1609480449412)(C:\Users\26284\AppData\Roaming\Typora\typora-user-images\image-20210101103709413.png)]![image-20210101103900884](http://img.yayi.site/csdn/c07fec57275b4d33686bb57fc21faa2e.png-watermaskStyle)

  xdebug 在php.ini 大概是这样子 重要的是端口号和zend_extension 和idekey

  idekey 是多人调试用到的

  端口号应该是xdebug收到连接就会发往9001端口（这个是phpstorm在监听）phpstorm默认监听了9003和9001端口。

  ![image-20210101104047868](http://img.yayi.site/csdn/de92046a9a2915e76b859e20bf090c35.png-watermaskStyle)

  

  - [ ] 之后打断点，点击运行调试

  ![image-20210101110815152](http://img.yayi.site/csdn/f98d3420da08ccc2e19a8c5e78704892.png-watermaskStyle)

  ​	再选择php脚本

  ​	或者：选择运行配置的话：php脚本

  ![image-20210101105330562](http://img.yayi.site/csdn/f56008c203e1ed2029e0ea42ba146868.png-watermaskStyle)

  到此结束，以下不用配了，不行再，参考

  ---

  

  

  > 顺便提一下
  >
  > ![image-20210101104243163](http://img.yayi.site/csdn/45a475a37b7e614a4cc1766b4ebd752f.png-watermaskStyle)
  >
  > cmd 乱码的话，问题不好找
  >
  > cmd命令行窗口显示中文乱码，多是因为cmd命令行窗口字符编码不匹配导致。
  >
  > 修改cmd窗口字符编码为UTF-8，命令行中执行：chcp 65001
  > 切换回中文：chcp 936
  > 这两条命令只在当前窗口生效，重启后恢复之前的编码。
  >
  > 切换cmd窗口字符编码有风险，例如切换过以后中文显示乱码，并且不能永久切换回原来模式，只能每次chcp 936。
  >
  >
  > phpstorm 的话好像
  >
  > IntelliJ IDEA creates files using the IDE encoding defined in the [File Encodings ](https://www.jetbrains.com/help/idea/settings-file-encodings.html)page of the **Settings / Preferences** dialog Ctrl+Alt+S. You can use either the system default or select from the list of available encodings. ==By default, this encoding affects console output.== If you want the encoding for console output to be different from the global IDE settings, configure the corresponding JVM



#### php-web类的本地调试。以thinkPHP5为例

使用xdebug. 

前提条件:php,xdebug  。 设置里选好配置解释器

https://www.jetbrains.com/help/phpstorm/zero-configuration-debugging.html#start-debugging-session



调试器：这个好像不用配

![image-20210101104646947](http://img.yayi.site/csdn/f163e6cc8070c9d07a0d871638394898.png-watermaskStyle)



这里 9001与php.ini 中对应。 注意9001端口是phpstorm启动的，是被连接者。什么时候启动？当你点击小电话时，就会启动。   ~~xdebug默认是9000~~

我们来证明一下：

未点击之前 ![image-20210101131920005](http://img.yayi.site/csdn/b29c47f5685eabaed24715f8e045f10e.png-watermaskStyle)

和点击之后

![image-20210101131856633](http://img.yayi.site/csdn/3c1aa3f4d91a6d53fe3a43d06a65706a.png-watermaskStyle)

![image-20210101104814475](http://img.yayi.site/csdn/e4d07bc2cc2b7eb622a5e19be93d39b5.png-watermaskStyle)

DBGp代理的是9001。

DBGp是什么。要配吗？

https://xdebug.org/docs/dbgpProxy

This tool allows you to proxy and route debugging request to IDEs depending on which IDE key is in use.

将php收到的路由和代理 到各种ides  哪个ide呢？ 取决于php.ini中的ide key 值与哪个ide中配置的idekey值 相等。这是在多人调试时？（有这样的应用场景？[有](https://derickrethans.nl/debugging-with-multiple-users.html
)）教程介绍看[jetbrains](https://www.jetbrains.com/help/phpstorm/multiuser-debugging-via-xdebug-proxies.html#configure-multiuser-debugging-via-an-xdebug-proxy-dbgp-server
)  

![Ps Xdebug Schema Proxy](http://img.yayi.site/csdn/d3d7bf3f6a82d9fa407845bc8d053452.png-watermaskStyle)

xdbug 有两种模式，单一ip （默认）和多ip。如果你单一ip ,不配置是可以的

![image-20210101105009708](http://img.yayi.site/csdn/d54216bb542c1c954b4508ed4d2d3dfc.png-watermaskStyle)

运行配置的话：php web application 

 

小电话,脚本的话， 要开启

小电话开启的是e [Languages & Frameworks | PHP | Debug](https://www.jetbrains.com/help/phpstorm/debug.html)

也就是上面phpstorm中的xdebug 配置端口

![image-20210101105235659](http://img.yayi.site/csdn/54247c5bde75de90a50157d0d4ec861b.png-watermaskStyle)





浏览器安装xdebug扩展,选择debug

配置一个 incoming Connection From <Debugging Engine>dialog,

配置一个web server

有几种情况：

+ 就地服务器，项目在服务器的document root 例如 /htdocs 。 你开发相当于直接在服务器上（The *document root* of an *in-place server* is the parent of the project root, either immediate or not. ）

+ 本地服务器。与上面不同的是这个要 复制资源到本地服务器目录。通常挂载方式。
+ 远程服务器。真正的远程。ip访问。use FTP/SFTP/FTPS protocols.

这里介绍就地，或者本地。

php-cgi是什么？ web server（如nginx）与php.exe是不能直接交互的，所以通过第三者交互。

更准确的来说，是一个遵循web server 协议（FastCGI或者CGI）的解析器，因为像nginx不能解决php为后缀的文件，只能交给第三方处理，以实现所谓扩展性。协议遵循 接受.php 输出 html 。参考：https://segmentfault.com/q/1010000008356979

php-cgi 和php-fpm 有什么不同，同是cgi 。协议不同和功能上有些差异。一个是CGI协议，一个是FastCGI。功能上各有优点，不能说谁好。

![image-20210101124757786](http://img.yayi.site/csdn/07d0ef4667b9c5fda1cae9f478310e0d.png-watermaskStyle)

嗯，没错，你还得配置nginx中的conf 指定php的cgi在哪里。

反正，我是自己手动启动ph.cgi的。phpstorm选择php web 运行配置时会帮你启动php-FCG。为什么phpstorm 不全套做完呢。麻烦死了。

总而言之，实现这个流程就行了

==浏览器（带一些识别区分信息，如xdbug扩展，intell的扩展，cookie,url session参数）->nginx->php-CGI->xdebug、php、DBGp->ide== 

返回时则逆过来就行了。

 参考：原文作者：Newiep
转自链接：https://learnku.com/articles/4090/the-first-step-to-becoming-a-senior-php-programmer-debugging-xdebug-principle
 

### 远程

差不多原理。改一下ip 。部署之类的。



总之。php脚本类型好像是装好xdebug就是最简单的了。
