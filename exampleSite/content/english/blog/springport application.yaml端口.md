---
title: springport application.yaml端口
date: 2020-10-08 21:06:20.000
updated: 2020-10-08 21:06:20.000
csdn_url: https://blog.csdn.net/weixin_43531940/article/details/108968506
description: 51
As explained in Spring documentation, there are several ways to do that:
Either you set the port in the command line (for example 8888)
-Dserver.port=8888 or --server.port=8888
Example : java -jar -Dserver.port=8888 test.jar
Or you set the port in the a
tags: java
categories: # springboot
article_id: 108968506
---
﻿51

As explained in Spring documentation, there are several ways to do that:

Either you set the port in the command line (for example 8888)

-Dserver.port=8888 or --server.port=8888

Example : java -jar -Dserver.port=8888 test.jar

Or you set the port in the application.properties

server.port=${port:4588}
or (in application.yml with yaml syntax)

server:
   port: ${port:4588}

---
Keep in mind that if your environment variables are MYPACKAGE_KEY_PUBLIC and MYPACKAGE_KEY_PRIVATE the keyname should only be MYPACKAGE_KEY.
heroku ssh key 

[https://devcenter.wercker.com/administration/environment-variables/ssh-keys/using-ssh-keys/](https://devcenter.wercker.com/administration/environment-variables/ssh-keys/using-ssh-keys/)
系统变量
