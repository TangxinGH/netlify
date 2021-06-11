---
title: html 标记分类字幕,css3新特性
date: 2021-05-11 10:30:51.000
updated: 2021-05-11 11:18:59.000
csdn_url: https://blog.csdn.net/weixin_43531940/article/details/116644079
description: <!DOCTYPE html> 意义
html 标记分类
html5 字幕 背景音乐 锚点链接
css3新特性
tags: css3新特性,html标记分类,总结
categories: 前端
article_id: 116644079
---
﻿[toc]
![s](http://img.yayi.site/csdn/ff8a0240106ea8f29f5ccd546439c1bd.gif-watermaskStyle)
>为什么html有容错性呢？
>曾经尝试过规范，结果xhtml成为了笑话。w3c 
>然后就有了html5
>所以`<!DOCTYPE html>` 是使成为一个html5文档。

# 标记分类
1. 分段标记：p
2. 换行标记：br
3. 标题标记 h
4. 对中标记：center
5. 块标记：div
6. 水平线标记：hr
7. 固定字体标记：粗体
8. 多媒体标记：img
9. 背景音乐标记：bgsound
10. 表格标记 
11. 字幕标记
	
	```bash
	<marquee></marquee>
	```
12. 表单标记：form,自带检验属性
13. 超链接,，描述图像（<a <img  ），文件链接（用于跳转），
14. 锚点链接，用于跳转本页面，`<a name='xxx'>xx</a>` `<a href='#xxx'>dd</a>`
15. 设计框架：
	>将文档分为若个窗格，如frame
	>框架集 frameset ，
	> 有安全问题，用xframe 限定。

# css
 样式有三种，优先级。
 挑选元素应用样式的，叫选择器，有很多种。标记符{规则表}
 ## 定义方法
  1. 内联style=''''
  2. `<style></style>`
  3. 文件中定义，`<link>`标签 rel  type href
  4. css @import声明导入
 ## 伪类
 如 a:hover {color:red}
 ## 样式继承和作用顺序
 ### 样式继承
  子继承父。如：被包含的就是子标记，包含的是父标记。
 ### ==作用顺序==
    1. 内联最高
    2. 按出现在html中或者被引用的顺序，出现越晚，就越高。
    3. 选择符从高到低：上下文选择符、类选择符、id选择符
    4. 没有则默认样式
    5. !important。强行覆盖样式。不建议用。
## css属性
1. 字体属性：如font-style是风格
2. 颜色与背景：如background-attachment：指定背景是否与页面一起动。默认scroll
3. 文本属性：letter-spacing 字符之间距离。常用的有text-align:justify 排列方式公平。vertical-align,垂直排列。text-indent 缩进。
4. 列表属性：list-style-type：空心圆。实体圆之类的。小写还是大写之类 的，还是list-style-img，图像作为项目号。悬挂缩进还是 position
5. 方框属性：margin (html文件内容与块元素的距离)、padding （html文件内容与边框距离 ）border 边界样式，
6. 定位属性：z-index 堆叠层。top left positon
## css3
新特性：
1.     不靠图片可以实现阴影之类的。
2. 盒容器变形。2D,3D
3. 独一无二的字体。@font-face。可以使用服务器的字体，而是不靠用户
4. 强大选择器：新增了10个选择器，多是伪类与属性选择器
5. 过渡与动画：平滑，不需要flash或者js
6. 媒体信息查询：得到用户设备信息。用于调整样式
7. 多列布局：弹性容器布局，像报纸哪样。

==毫无疑问选择html5+css3==

