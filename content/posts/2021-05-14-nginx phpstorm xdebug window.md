
太痛苦了。搞了一天。
教程差不多。
说几个注意点：

 1.  phpstorm 中的validate 这个验证。path to create validation script 填你ide的目录。

![在这里插入图片描述](http://img.yayi.site/csdn/20200510090832672.png-watermaskStyle)

 1. 我把 mappings 关了，有什么影响不知道。
![在这里插入图片描述](http://img.yayi.site/csdn/20200510091238526.png-watermaskStyle)
![在这里插入图片描述](http://img.yayi.site/csdn/20200510091017465.png-watermaskStyle)
 3. 关键的一点
 	nginx .conf 中配置，php 文件为后缀的交给 cgi 处理。原本的 fastcgi_param 是这样的。
fastcgi_param  SCRIPT_FILENAME  ==/scripts==$fastcgi_script_name;  然而 nginx下并没有scripts 目录。会报No input file specified.[https://blog.51cto.com/xiahongyuan/852424](https://blog.51cto.com/xiahongyuan/852424)
主要是我的php新下的。配置是原来的官方。所以我改成了：
```
 # 设置自定义变量的方法 
	   set $phpstorm_root  E:\WorkPlacePHPStorm/learn/HelloWord/ ;
       location ~ \.php$ {
           fastcgi_pass   127.0.0.1:9000;
            fastcgi_index  index.php;
            fastcgi_param  SCRIPT_FILENAME  $phpstorm_root$fastcgi_script_name;
            include        fastcgi_params;
        }

```
如果在上面的phystorm中的mapping  中把ide项目的目录映射到nginx的script下，是不是也可以呢。好像不可以。看来每次都得改啊。
==要php后缀的urL 才会进入cgi ，除非你改所有文件全部进cgi==

还有一点，并没有开启cgi 。上文提到，交给cgi ，所以php.cgi 要开启。至于，它会自动开启还是手动开。我就不知道了。反正我是手动的。默认 9000端口。所以php.ini 中的xdebug要改成，9001 。phpstorm 
![在这里插入图片描述](http://img.yayi.site/csdn/20200510092436735.png-watermaskStyle)
==注意这个dbgp 的是niginx监听的端口==
=![在这里插入图片描述](http://img.yayi.site/csdn/2020051009245639.png-watermaskStyle)
我觉得应该先理解xdebug的原理。

 ## debug
 niginx 中设置一下超时时间。默认是60s
 debug时间可能不够

```
fastcgi_connect_timeout 180;
 
			fastcgi_read_timeout 180;
 
			fastcgi_send_timeout 180;
```

## 不开启 nginx.conf 中的cgi 的会报错

An error occurred.
Sorry, the page you are looking for is currently unavailable.
Please try again later.

If you are the system administrator of this resource then you should check the error log for details.

Faithfully yours, nginx.

2020/05/10 09:51:16 [error] 13352#12912: *50 connect() failed (10061: No connection could be made because the target machine actively refused it) while connecting to upstream, client: 127.0.0.1, server: localhost, request: "GET /index.php?XDEBUG_SESSION_START=14949 HTTP/1.1", upstream: "fastcgi://127.0.0.1:9000", host: "localhost:7878"

写个bat文件自动开启？php.cgi.exe? RunHiddenConsole 是个隐藏控制台的程序》？
[
https://www.nginx.com/resources/wiki/start/topics/examples/phpfastcgionwindows/](https://www.nginx.com/resources/wiki/start/topics/examples/phpfastcgionwindows/)

nginx的脚本倒有一个[https://www.jianshu.com/p/40985adfe029](https://www.jianshu.com/p/40985adfe029)

```powershell
:: 关闭回显，即执行本脚本时不显示执行路径和命令，直接显示结果
@echo off
rem @author luwuer
::bat文件右键用“ 编辑” ?打开，

::另存为时，UTF-8保存为ANSI 格式。即可解决运行是乱码问题，


::————————————————
::版权声明：本文为CSDN博主「yang889999888」的原创文章，遵循CC 4.0 BY-SA版权协议，转载请附上原文出处链接及本声明。
::原文链接：https://blog.csdn.net/yang889999888/article/details/72934787

color f8
set NGINX_DIR=E:\WorkPlacePHPStorm\nginx18\

:INFO
  echo.
  echo --------------------- 进程列表 ---------------------
  tasklist|findstr /i "nginx.exe"
  if errorlevel 1 echo nginx未启动
  echo --------------------- 进程列表 ---------------------

  echo.
  echo. 1. 启动Nginx
  echo. 2. 关闭Nginx
  echo. 3. 重启Nginx
  echo. 4. 退出
  echo.
  echo 请输入功能序号：
  set /p id=
    if "%id%"=="1" goto START
    if "%id%"=="2" goto STOP
    if "%id%"=="3" goto RESTART
    if "%id%"=="4" exit
  pause

:START 
  if exist "%NGINX_DIR%nginx.exe" (
    cd /d %NGINX_DIR%
    start "" nginx.exe
    echo 启动成功
  ) else (
    echo "%NGINX_DIR%nginx.exe不存在"
  )
  goto INFO

:STOP
  taskkill /F /IM nginx.exe > nul
  echo 已关闭所有nginx进程
  goto INFO

:RESTART
  taskkill /F /IM nginx.exe > nul
  if exist "%NGINX_DIR%nginx.exe" (
    cd /d %NGINX_DIR%
    start "" nginx.exe
  ) else (
    echo "%NGINX_DIR%nginx.exe不存在"
  )
  echo 已重启
  goto INFO

goto :eof
```

## phpstorm自带server
![在这里插入图片描述](http://img.yayi.site/csdn/20200510104529955.png-watermaskStyle)
点击这个好像启动自带的服务器。打断点好像也能终止。所以不用nginx也行的。浏览器的xdebug也没有。我都是本地项目。没涉及到远程的东西。
应该是默认连接了php-cgi 的9000端口？好像关我手动开的cgi了，依然工作。可能phpstorm 的自带server 开启了cgiphp ？ 越来越迷惑了？？？？ 只要打开小电话就行？？

![在这里插入图片描述](http://img.yayi.site/csdn/20200510105500473.png-watermaskStyle)
应该是它自己开了一个php cgi的端口监听吧

那我前面又nginx 又cgi的不白弄了吗？？？

---

整理一下。
## 第一步
下载php 区分线程安全和非安全。
## 第二
下载 xdebug 对应版本。dll
放到 php 的ext 文件下。
复制php.devolement.ini 为php.ini 编辑 php ini  
增加 xdebug 配置。[https://www.jetbrains.com/help/phpstorm/2020.1/configuring-xdebug.html?utm_source=product&utm_medium=link&utm_campaign=PS&utm_content=2020.1](https://www.jetbrains.com/help/phpstorm/2020.1/configuring-xdebug.html?utm_source=product&utm_medium=link&utm_campaign=PS&utm_content=2020.1)
：host 和端口 localhost 端口写 9001 这个在phpstorm中要埴。
xdebug.remote_enable=1 enable on 
还有一个zend_extension=<path_to_zend_debugger> 刚才的ext文件下。
反正 先配置主要的。就行
自己检查安装成功与否。

## 第三
配置phpstorm 
![在这里插入图片描述](http://img.yayi.site/csdn/20200510110707121.png-watermaskStyle)
解析器写 你刚才下载php版本。
![在这里插入图片描述](http://img.yayi.site/csdn/20200510110750830.png-watermaskStyle)
填9001 

## 第四 
phpstorm中
打断点：
![在这里插入图片描述](http://img.yayi.site/csdn/20200510110847728.png-watermaskStyle)
打开小电话：右上角
![在这里插入图片描述](http://img.yayi.site/csdn/20200510110932897.png-watermaskStyle)
点击一个浏览器
![在这里插入图片描述](http://img.yayi.site/csdn/20200510110856938.png-watermaskStyle)
就可以了。
用phystorm 自带的省掉不少。学习环境就用这个吧。其它环境，什么远程调试。百度吧。
