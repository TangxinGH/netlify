---
title: putty 方便技巧ssh
date: 2020-03-28 20:37:24.000
updated: 2020-03-28 20:37:24.000
csdn_url: https://blog.csdn.net/weixin_43531940/article/details/105167868
description: 
tags: 
categories: Linux
article_id: 105167868
---
﻿
# 这是修改版的putty

[使用教程](https://blog.csdn.net/xhhjin/article/details/8447076?depth_1-utm_source=distribute.pc_relevant.none-task&utm_source=distribute.pc_relevant.none-task)

Putty 默认版只能保存登陆名，每次需输入登陆密码，主机和登陆名是保存在注册表中的。不过因为它是开源，所以有相关需求者做了个能同时保存用户和密码的版本，这些信息是保存在文件中的。该保存登陆名和密码版可在些下载：putty_v6.0.rar。

就是设置起来有点是特别好理解，默认版本也是这样子的。操作步骤全写在下面这幅图片里了：![](http://img.yayi.site/csdn/aHR0cHM6Ly9yYXcuZ2l0aHVidXNlcmNvbnRlbnQuY29tL1RhbmdYaW5HaXRodWIvcGljYmVkL21hc3Rlci9pbWcvMjAyMDA1MjUyMjMwMTEuanBn-watermaskStyle)


可以看看人家是怎么改的 PuTTY 源代码的： 修改Putty 0.6 代码支持SSH 密码保存功能
------------------------------------------------

版权声明：本文为CSDN博主「艾蔓草」的原创文章，遵循 CC 4.0 BY-SA 版权协议，转载请附上原文出处链接及本声明。
原文链接：https://blog.csdn.net/xhhjin/article/details/8447076

# 保活

有很多朋友使用putty来远程链接来操作，正当桌面不停刷屏滚动的时候，不到几分钟putty就自动断开了。或许有些小苦恼。今天教大家通过putty一个小设置轻松解决这个问题，让链接不再轻易断开。希望对做网站的朋友有所帮助！
打开putty，在 Connection 里面有个 Seconds between keepaliaves，这里就是每间隔指定的秒数，就给服务器发送一个空的数据包，来保持连接。以免登录的主机那边在长时间没接到数据后，会自动断开 SSH 的连接。

如图：默认是0 表示禁用
------------------------------------------------

版权声明：本文为CSDN博主「qq_36149805」的原创文章，遵循 CC 4.0 BY-SA 版权协议，转载请附上原文出处链接及本声明。
原文链接：https://blog.csdn.net/qq_36149805/article/details/79136045

![img](http://img.yayi.site/csdn/aHR0cHM6Ly9yYXcuZ2l0aHVidXNlcmNvbnRlbnQuY29tL1RhbmdYaW5HaXRodWIvcGljYmVkL21hc3Rlci9pbWcvMjAyMDA1MjYyMDMwNTUucG5n-watermaskStyle)

# putty窗口解决中文乱码问题

putty的默认设置不支持中文显示，我们可以通过配置putty解决这个问题。

我们先确认主机的编码方式，在putty中输入如下命令：

echo $LANG$LANGUAGE

得到：

zh_CN.UTF-8

说明这台主机用的是UTF-8编码。

下面开始设置putty：
在窗口标题点击右键，选择 Change Setting...

分别点击Appearance和Translation：

点击Change，选择中文字体即可，比如新宋体。

在Received data assumed to be in which character set:下拉单中选择UTF-8，点击Apply保存，这时putty应该就可以支持中文显示了。
------------------------------------------------

版权声明：本文为CSDN博主「Young_2717」的原创文章，遵循 CC 4.0 BY-SA 版权协议，转载请附上原文出处链接及本声明。
原文链接：https://blog.csdn.net/imyang2007/article/details/7780182

---

==只需要将session文件下的配置好的文件复制一份，改个主机?密码，然后就不用一遍遍设置==！！！！！

---

使用帮助 

在窗口中有一个？号，点击 后，再点击窗口内的内容就么找到相应的帮助

![image-20200414134127820](http://img.yayi.site/csdn/aHR0cHM6Ly9yYXcuZ2l0aHVidXNlcmNvbnRlbnQuY29tL1RhbmdYaW5HaXRodWIvcGljYmVkL21hc3Rlci9pbWcvMjAyMDA1MjYyMDMzMTcucG5n-watermaskStyle)

[外链图片转存失败,源站可能有防盗链机制,建议将图片保存下来直接上传(img-OmIRJtNa-1590496556033)(https://raw.githubusercontent.com/TangXinGithub/picbed/master/img/20200526203305.jpg)]
---

### 修改窗口大小

![img](http://img.yayi.site/csdn/aHR0cHM6Ly9yYXcuZ2l0aHVidXNlcmNvbnRlbnQuY29tL1RhbmdYaW5HaXRodWIvcGljYmVkL21hc3Rlci9pbWcvMjAyMDA1MjYyMDMyNDYucG5n-watermaskStyle)

---

但是现在没有保存，这次使用是正常的，下次打开的时候，又返回默认设置了。 之前一直没搞清楚这点。所以凑合用了很长时间。 保存的步骤如下：

\1.    修改配置

\2.    点session 返回主界面

\3.    ==选中要保存的session。== 这里是10.85.10.1

\4.    点save。

\5.    Ok ，下次在登陆10.85.10.1时，就是自己喜欢的配置了。 当然如果修改Default Settings， 以后新建的session都是修改之后的session了。

**Yasi：注意，下图中，要想将当前填写的10.85.10.1保存到配置中，必须在Saved Sessions编辑框中填写一个名称，如 "10.85.10.1 - testing"，然后点Save才能保存。否则保存无效！**

![image-20200414135259192](http://img.yayi.site/csdn/aHR0cHM6Ly9yYXcuZ2l0aHVidXNlcmNvbnRlbnQuY29tL1RhbmdYaW5HaXRodWIvcGljYmVkL21hc3Rlci9pbWcvMjAyMDA1MjYyMDMxMTMucG5n-watermaskStyle)

### 新的session

默认设置是这个

![image-20200414135622174](http://img.yayi.site/csdn/aHR0cHM6Ly9yYXcuZ2l0aHVidXNlcmNvbnRlbnQuY29tL1RhbmdYaW5HaXRodWIvcGljYmVkL21hc3Rlci9pbWcvMjAyMDA1MjYyMDMxMTkucG5n-watermaskStyle)

load 它就可以修改了。

---

我们一般使用 PuTTY 等 SSH 客户端来远程管理 Linux  服务器。但是，一般的密码方式登录，容易有密码被暴力破解的问题。所以，一般我们会将 SSH 的端口设置为默认的 22 以外的端口，或者禁用  root 账户登录。其实，有一个更好的办法来保证安全，而且让你可以放心地用 root 账户从远程登录——那就是通过密钥方式登录。

密钥形式登录的原理是：利用密钥生成器制作一对密钥——一只公钥和一只私钥。将公钥添加到服务器的某个账户上，然后在客户端利用私钥即可完成认证并登录。这样一来，没有私钥，任何人都无法通过 SSH 暴力破解你的密码来远程登录到系统。此外，如果将公钥复制到其他账户甚至主机，利用私钥也可以登录。

下面来讲解如何在 Linux 服务器上制作密钥对，将公钥添加给账户，设置 SSH，最后通过客户端登录。



### 1. 制作密钥对

首先在服务器上制作密钥对。首先用密码登录到你打算使用密钥登录的账户，然后执行以下命令：

```
[root@host ~]$ ssh-keygen  <== 建立密钥对
Generating public/private rsa key pair.
Enter file in which to save the key (/root/.ssh/id_rsa): <== 按 Enter
Created directory '/root/.ssh'.
Enter passphrase (empty for no passphrase): <== 输入密钥锁码，或直接按 Enter 留空
Enter same passphrase again: <== 再输入一遍密钥锁码
Your identification has been saved in /root/.ssh/id_rsa. <== 私钥
Your public key has been saved in /root/.ssh/id_rsa.pub. <== 公钥
The key fingerprint is:
0f:d3:e7:1a:1c:bd:5c:03:f1:19:f1:22:df:9b:cc:08 root@host
```

密钥锁码在使用私钥时必须输入，这样就可以保护私钥不被盗用。当然，也可以留空，实现无密码登录。

现在，在 root 用户的家目录中生成了一个 .ssh 的隐藏目录，内含两个密钥文件。id_rsa 为私钥，id_rsa.pub 为公钥。

### 2. 在服务器上安装公钥

键入以下命令，在服务器上安装公钥：

```
[root@host ~]$ cd .ssh
[root@host .ssh]$ cat id_rsa.pub >> authorized_keys
```

如此便完成了公钥的安装。为了确保连接成功，请保证以下文件权限正确：

```
[root@host .ssh]$ chmod 600 authorized_keys
[root@host .ssh]$ chmod 700 ~/.ssh
```

### 3. 设置 SSH，打开密钥登录功能

编辑 /etc/ssh/sshd_config 文件，进行如下设置：

```
RSAAuthentication yes
PubkeyAuthentication yes
```

另外，请留意 root 用户能否通过 SSH 登录：

```
PermitRootLogin yes
```

当你完成全部设置，并以密钥方式登录成功后，再禁用密码登录：

```
PasswordAuthentication no
```

最后，重启 SSH 服务：

```
[root@host .ssh]$ service sshd restart
```

### 4. 将私钥下载到客户端，然后转换为 PuTTY 能使用的格式

使用 WinSCP、SFTP 等工具将私钥文件 id_rsa 下载到客户端机器上。然后打开 PuTTYGen，单击 Actions 中的 Load 按钮，载入你刚才下载到的私钥文件。如果你刚才设置了密钥锁码，这时则需要输入。

载入成功后，PuTTYGen 会显示密钥相关的信息。在 Key comment 中键入对密钥的说明信息，然后单击 Save private key 按钮即可将私钥文件存放为 PuTTY 能使用的格式。

今后，当你使用 PuTTY 登录时，可以在左侧的 Connection -> SSH -> Auth 中的 Private key  file for authentication: 处选择你的私钥文件，然后即可登录了，过程中只需输入密钥锁码即可。

---

### 非root用户等其它 用户登录ssh 私钥

首先切换到相应用户下su 用户名 下

然后 sshd-gen之类的生成。默认生成在用户主目录下的.ssh下这是个隐藏目录。ls -l 

然后直接 cat 用户主目录/id_rsa.pub >> /用户主目录/.ssh/authorized_keys  。这样就是注册了。不然后显示：==所选的用户密钥未在远程主机上注册。请再试一次==


