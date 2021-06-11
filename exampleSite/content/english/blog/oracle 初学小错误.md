Error 6 initializing SQL*Plus SP2-0667: Message file sp1<lang>.msb not found SP2-0750: You may need to set ORACLE_HOME to your Oracle software directory

linux下要su权限才行,切换到root下，再切回oracle下
window下，百度吧

[参考教程](https://www.w3cschool.cn/oraclejc/oraclejc-gpa52qqy.html)
* 创建用户，在超级管理员下创建。creat user
* 然后授于权限 grant
* 登录 connect ot@SID
 	* 5 在命令提示符以 OS身份连接
connect / as sysdba
6 以 SYSTEM的身份连接
connect system/xxxxxxx@ 服务名
* 
* ![在这里插入图片描述](http://img.yayi.site/csdn/20200310180316327.png-watermaskStyle)
==* 好吧，还是xshell好用，有很多功能。虽然putty简洁。复制简单。putty不保活==


[被拒--悲剧之ORA-01017: invalid username/password; logon denied 错误](https://www.cnblogs.com/pangting/p/7027492.html)
这个错误有很多原因，我的是用户名大小写问题。
![在这里插入图片描述](http://img.yayi.site/csdn/20200318170313727.png-watermaskStyle)
用户存在
![在这里插入图片描述](http://img.yayi.site/csdn/20200318170338972.png-watermaskStyle)
更改密码的时候。用户是大写的learn .所以是大小写的问题。
加上""可以解决。或者关闭大小写用户登录敏感。
![在这里插入图片描述](http://img.yayi.site/csdn/20200318170529386.png-watermaskStyle)
oracle数据库无法连接 The Network Adapter could not establish
[Caused by: java.sql.SQLException: Io 异常: The Network Adapter could not establish the connection](https://www.cnblogs.com/dingjiaoyang/p/6378088.html)

我的情况是防火墙没放行1521端口。真想关了防火墙
