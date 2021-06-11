---
title: js网络变化
date: 2019-10-16 13:23:47.000
updated: 2019-10-16 13:25:24.000
csdn_url: https://blog.csdn.net/weixin_43531940/article/details/102583754
description: window.ononline = function() {
				alert("链接上网络了");
			}
			window.onoffline = function() {
				alert("网络链接已断开");
			}

    // Your code here...
    window.addEventListener('online', function(){
    a...
tags: 
categories: javaweb
article_id: 102583754
---
﻿

```javascript
window.ononline = function() {
				alert("链接上网络了");
			}
			window.onoffline = function() {
				alert("网络链接已断开");
			}

    // Your code here...
    window.addEventListener('online', function(){
    alert('网络连接恢复！');
})
window.addEventListener('offline', function(){
    alert('网络连接中断！');
})
```

只能判断网线插拨，不能判断ping通
