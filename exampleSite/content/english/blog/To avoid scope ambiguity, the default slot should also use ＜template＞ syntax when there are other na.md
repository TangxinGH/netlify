---
title: To avoid scope ambiguity, the default slot should also use ＜template＞ syntax when there are other na
date: 2020-10-04 19:05:32.000
updated: 2020-10-04 19:05:32.000
csdn_url: https://blog.csdn.net/weixin_43531940/article/details/108921358
description: 具名插槽
https://cn.vuejs.org/v2/guide/components-slots.html
&lt;base-layout&gt;
  &lt;template v-slot:header&gt; // slot="" 已经废弃 。！！！！
    &lt;h1&gt;Here might be a page title&lt;/h1&gt;
  &lt;/template&gt;

  &lt;p&gt;A paragraph for the main content.&lt;/p&
tags: vue slot,slot,插槽：
categories: 前端
article_id: 108921358
---
﻿### 具名插槽
[https://cn.vuejs.org/v2/guide/components-slots.html](https://cn.vuejs.org/v2/guide/components-slots.html)

```html
<base-layout>
  <template v-slot:header> // slot="" 已经废弃 。！！！！
    <h1>Here might be a page title</h1>
  </template>

  <p>A paragraph for the main content.</p>
  <p>And another one.</p>

  <template v-slot:footer>
    <p>Here's some contact info</p>
  </template>
</base-layout>
```
==base-layout 是一个子组件。内容如下：

```html
<div class="container">
  <header>
    <slot name="header"></slot> // 当有多个slot 并且name 时 上面的就要写多个tempelte 了
  </header>
  <main>
    <slot></slot>
  </main>
  <footer>
    <slot name="footer"></slot>
  </footer>
</div>
```

