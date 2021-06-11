---
title: bing图片
date: 2019-11-14 09:22:05.000
updated: 2019-11-14 09:22:05.000
csdn_url: https://blog.csdn.net/weixin_43531940/article/details/103061371
description: https://github.com/xCss/bing/blob/master/readme.md
浏览器会有跨域请求限制
参数是第一个是加？ 第二个开始是&amp;
callback用来jsonp


tags: 
categories: javaweb
article_id: 103061371
---
﻿[https://github.com/xCss/bing/blob/master/readme.md](https://github.com/xCss/bing/blob/master/readme.md)

浏览器会有跨域请求限制

参数是第一个是加？ 第二个开始是&
callback用来jsonp

注意参数 int
有多个接口，不能混用

不要频繁的请求
https://bing.ioliu.cn/v1?d=1&w=800&h=600
最好不要指定分辨率 


```css
<script>--%>


        <%--for (let i = 0; i < 7; i++) {--%>
       <%--setTimeout( function () {--%>

            <%--document.getElementById("bing" + (i + 1)).setAttribute("src", "http://bing.ioliu.cn/v1?d="+i);--%>



            <%--},5000);--%>
        <%--}--%>



<%--</script>--%>

```
jsOn 用object，还是array方便？ 
[https://www.cnblogs.com/jpfss/p/9056485.html](https://www.cnblogs.com/jpfss/p/9056485.html)

```java
 @RequestMapping("/bingImg")
    public void bingImg(HttpServletResponse response ,HttpServletRequest request ) throws IOException {
        JSONArray jsonArray = new JSONArray();
        request.setCharacterEncoding("utf-8");
        response.setHeader("Content-type", "application/json;charset=utf-8");
        PrintWriter out = response.getWriter();
for (int i=0;i<7;i++)
        {
        String  httpUrl=" https://cn.bing.com/HPImageArchive.aspx?format=js&idx="+i+"&n=1&mkt=zh-CN";

          String j= ONEAPI.request(httpUrl,null);// my http request
//构造json

            jsonArray.add(i,JSON.parseObject(j));
    }

        out.write("localHandler("+jsonArray.toJSONString()+")");
System.out.println(jsonArray.toJSONString());
```
![在这里插入图片描述](http://img.yayi.site/csdn/20191114113941454.png-watermaskStyle)

layui最好自适应，不要设置height，不然图片显示不出来，为什么？
![在这里插入图片描述](http://img.yayi.site/csdn/20191114130551419.png-watermaskStyle)




```css
<%--布局还真是引入问题，自己的的居然不行。为什么--%>
    <!-- 最新版本的 Bootstrap 核心 CSS 文件 -->
    <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/bootstrap@3.3.7/dist/css/bootstrap.min.css" integrity="sha384-BVYiiSIFeK1dGmJRAkycuHAHRg32OmUcww7on3RYdg4Va+PmSTsz/K68vbdEjh4u" crossorigin="anonymous">

    <!-- 可选的 Bootstrap 主题文件（一般不用引入） -->
    <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/bootstrap@3.3.7/dist/css/bootstrap-theme.min.css" integrity="sha384-rHyoN1iRsVXV4nD0JutlnGaslCJuC7uwjduW9SVrLvRYooPp2bWYgmgJQIXwl/Sp" crossorigin="anonymous">

    <!-- 最新的 Bootstrap 核心 JavaScript 文件 -->
    <script src="https://cdn.jsdelivr.net/npm/bootstrap@3.3.7/dist/js/bootstrap.min.js" integrity="sha384-Tc5IQib027qvyjSMfHjOMaLkfuWVxZxUPnCJA7l2mCWNIpG9mGCD8wGNIcPD7Txa" crossorigin="anonymous"></script>

```

看官方文档



js获取子元素不要用childnode, 这个有兼容性问题，反正我的p标签无法，调试时候好像又找得到，用jquery,  用第三方好？原生不好？
![在这里插入图片描述](http://img.yayi.site/csdn/20191114150614143.png-watermaskStyle)
好像我的jsonp 都不执行输出console.log的。。。。
