---
title: nigx代理解决跨域问题，vuecli axios 直接跨域，开发环境下调试跨域
date: 2019-12-27 18:16:48.000
updated: 2019-12-27 18:16:48.000
csdn_url: https://blog.csdn.net/weixin_43531940/article/details/103734826
description: https://www.cnblogs.com/lovesong/p/10269793.html

server{
        listen 8888;
        server_name  192.168.1.100;
 
        location /{
            proxy_pass http://192.168.1.100:8080;
        }
 
 ...
tags: nginx
categories: 网络
article_id: 103734826
---
﻿[https://www.cnblogs.com/lovesong/p/10269793.html
](https://www.cnblogs.com/lovesong/p/10269793.html)


```bash
server{
        listen 8888;
        server_name  192.168.1.100;
 
        location /{
            proxy_pass http://192.168.1.100:8080;
        }
 
        location /api{
            proxy_pass http://ni.hao.sao/api;
        }
    }
```
vue cli +axios 中，可以

开发环境用：![在这里插入图片描述](http://img.yayi.site/csdn/20200106185843529.png-watermaskStyle)

注意，这样只能在开发环境，有用，如果要在生产环境，用nginx 或者用下面的方法。

[https://blog.csdn.net/d295968572/article/details/80764216](https://blog.csdn.net/d295968572/article/details/80764216)

pathRewirte的理解。
https://blog.csdn.net/weixin_40920953/article/details/85150784


建议在 开发环境前后端联调。不用每次打包，，build ，麻烦

https://blog.csdn.net/d295968572/article/details/80764216 中那个开发环境中我们用自己api，生产环境下用正常的接口地址，
这个有点麻烦，不知道说什么。

 proxy_pass的斜杠问题
[https://segmentfault.com/a/1190000020027003](https://segmentfault.com/a/1190000020027003)

因为vue 中改 api 后端地址也麻烦，要重新 npm run dev 
所以用 nginx 来代理一下。

vue config/index.js中
```bash
env:require('./dev.env'),//这个是跨域加上去的,包括下面的proxyTable内容
    // Paths
    assetsSubDirectory: 'static',
    assetsPublicPath: '/',
    proxyTable: {
		'/api':{
			target:'http://0.0.0.0:8085',//这里放了nginx ,nginx中设置了可以跨域,nginx 代理会去找真正的服务,为了不修改这里而重启麻烦而用nginx作了代理
			changeOrigin:true,
			
		}
		
	},
```


#解决跨域问题，代理
		location /api {
			
			#代理配置参数
			      proxy_connect_timeout 280;
			      proxy_send_timeout 280;
			      proxy_read_timeout 280;
			      proxy_set_header Host $host;
			      proxy_set_header X-Forwarder-For $remote_addr;
			   proxy_pass http://127.0.0.1:3000/api;
			
			
			#跨域相关设置
			 add_header 'Access-Control-Allow-Origin' '*' always;
			      add_header 'Access-Control-Allow-Credentials' 'true';
			      add_header 'Access-Control-Allow-Headers' 'Origin, X-Requested-With, Content-Type, Accept' always;
			
			
			
			
          
           
        }


```bash
https://segmentfault.com/a/1190000020027003
```

