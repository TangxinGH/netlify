---
title: innerhtml bokeh 不起作用 script src
date: 2021-04-09 18:36:46.000
updated: 2021-04-09 20:11:22.000
csdn_url: https://blog.csdn.net/weixin_43531940/article/details/115557051
description: innerhtml 不起作用。
div 和iframe 的innerhtml和write 都 没有用
write 没有用
iframe write 和innerhtml没有用
用iframe 的srcdoc 可以。src 可以是可以。需求不行。

什么文献都是英文的。。。。
Note: script elements inserted using innerHTML do not execute when they are inserted.
html5中在innerHTML中不会执行插入的脚本
crea.
tags: js
categories: JavaScript
article_id: 115557051
---
﻿1. innerhtml 不起作用。
2. div 和iframe 的innerhtml和write 都 没有用
3. write 没有用
4. iframe write 和innerhtml没有用
5. 用iframe 的srcdoc 可以。src 可以是可以。需求不行。

[什么文献都是英文的。。。。](https://www.w3.org/TR/2008/WD-html5-20080610/dom.html#innerhtml0)
Note: script elements inserted using innerHTML do not execute when they are inserted.
html5中在innerHTML中不会执行插入的脚本

[createElement 会触发渲染事件，所以会被 加载 ](https://ghinda.net/article/script-tags/)

 scripts[i].src//得到src，下载 eval 执行。下载 要跨源。 
或者 使用boken的内联方法
"CDN",
    "INLINE",

---

调用 eval()方法

或者这种
var newScript = document.createElement("script");
newScript.src = "http://www.example.com/my-script.js";
target.appendChild(newScript);

你们澄清一下——我已经看到很多答案使用 appendChild，我想让你们知道它完全可以作为 append

 const html =
    `<script>
        alert('👋 there ! Wanna grab a 🍺'); 
    </script>`;

  const scriptEl = document.createRange().createContextualFragment(html);
  parent.append(scriptEl);
[详细见](https://stackoverflow.com/questions/1197575/can-scripts-be-inserted-with-innerhtml)

---
Uncaught ReferenceError: Bokeh is not defined
果然


