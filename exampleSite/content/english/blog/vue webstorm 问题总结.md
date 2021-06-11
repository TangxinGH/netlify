---
title: vue webstorm 问题总结
date: 2020-01-02 22:48:41.000
updated: 2020-01-02 22:48:41.000
csdn_url: https://blog.csdn.net/weixin_43531940/article/details/103697331
description: WebStorm光标经常变成块状更改
https://blog.csdn.net/alokka/article/details/73719371
insert
Parsing error: x-invalid-end-tag
ivew，tmd rubbish
这个我也无法解决，我关了eslint也没用，只能手动关标签

...
tags: vue,html,js,vue.js,node.js
categories: 前端
article_id: 103697331
---
﻿WebStorm光标经常变成块状更改
https://blog.csdn.net/alokka/article/details/73719371
insert

Parsing error: x-invalid-end-tag
ivew，tmd rubbish
这个我也无法解决，我关了eslint也没用，只能手动关标签
这个好像可以解决，
[https://www.cnblogs.com/midnight-visitor/p/9590358.html](https://www.cnblogs.com/midnight-visitor/p/9590358.html)
![在这里插入图片描述](http://img.yayi.site/csdn/20191225191705884.png-watermaskStyle)package.json中改一下，反正有的都改


这些也可以自己定义，全部off 是最好的
"rules": {
	"generator-star-spacing": "off",
	"no-tabs":"off",
	"no-unused-vars":"off",
	"no-console":"off",
	"no-irregular-whitespace":"off",
	"no-debugger": "off"
},
————————————————
版权声明：本文为CSDN博主「舜岳」的原创文章，遵循 CC 4.0 BY-SA 版权协议，转载请附上原文出处链接及本声明。
原文链接：`https://blog.csdn.net/qq_41614928/article/details/102787344`

如果你遇到了这个错误，作用cli,请你先备份一份你的项目，这是个好习惯，

```
vue的npm ERR! missing script: dev
```

init 是重置？？
备份是个好习惯



vue中 传 到 mock.js ，取值发生了Undefined，js对象到mock.js 再到js??
反正试一下吧 ` var json=JSON.parse(options.body);`

 这个不行，var json=eval(options.body);

同级视图，很有用。==记录路由带s复数==
[
https://router.vuejs.org/zh/guide/essentials/named-views.html](https://router.vuejs.org/zh/guide/essentials/named-views.html)


官方的文档一定要看
![在这里插入图片描述](http://img.yayi.site/csdn/2019122721121614.png-watermaskStyle)

当我想在一个组件加载完成后执行一些方法，由于我是小白的原因，组件之前、父子、兄弟之间传不了参数，主要不知道怎么传，使用了这个mounted 钩子函数，相当于jquary的ready（）函数。


webstorm 调试，当发生异常的时候，断点，
![在这里插入图片描述](http://img.yayi.site/csdn/20191228093155508.png-watermaskStyle)
![在这里插入图片描述](http://img.yayi.site/csdn/20191228093210971.png-watermaskStyle)

anY


ivew tmd 这些文档就不能写清楚点吗，
on-select的用法
应该是回调函数，只用提供方法名就行，不用定义参数![在这里插入图片描述](http://img.yayi.site/csdn/20191228095038658.png-watermaskStyle)
[https://blog.csdn.net/jjw_zyfx/article/details/102310448](https://blog.csdn.net/jjw_zyfx/article/details/102310448)


selection是已经选择的数据==包括== currentRow

![在这里插入图片描述](http://img.yayi.site/csdn/20191228100705612.png-watermaskStyle)

ivew手动修改 表格的值是不会渲染的，
[https://www.cnblogs.com/surui/p/9038543.html](https://www.cnblogs.com/surui/p/9038543.html)
[https://blog.csdn.net/panyang01/article/details/76665448](https://blog.csdn.net/panyang01/article/details/76665448)


问题：
之前使用的+ 进行连接，如： console.log("前端参数param是："+self.filters.ip)
显示结果是：   [object Object]    

 
解决方案：

```bash
在VUE文件中，打印拼接的原始数据用  ， 隔开，如
console.log("前端参数param是："，self.filters.ip)
结果即可正常显示：
```


————————————————
版权声明：本文为CSDN博主「~say hello」的原创文章，遵循 CC 4.0 BY-SA 版权协议，转载请附上原文出处链接及本声明。
原文链接：https://blog.csdn.net/weixin_43295950/article/details/97678836

 component lists rendered with v-for should have explicit keys.：
 
https://blog.csdn.net/qq_36069339/article/details/82191472



Avoid mutating a prop directly since the value will be overwritten whenever the parent component re-renders. Instead, use a data or computed property based on the prop's value. Prop being mutated: "value2"

什么鬼
    所有的 prop 都使得其父子 prop 之间形成了一个单向下行绑定：父级 prop 的更新会向下流动到子组件中，但是反过来则不行。（父组件更新，子组件中的prop值也会更新，但子组件不能修改由父组件传递过来的值）

 解决办法：

    定义一个本地的 data 属性并将这个 prop 用作其初始值，同步对组件的修改，再通知父组件更新
相关代码：
————————————————
版权声明：本文为CSDN博主「ST92」的原创文章，遵循 CC 4.0 BY-SA 版权协议，转载请附上原文出处链接及本声明。
原文链接：https://blog.csdn.net/qq_36938056/article/details/86526352


ivew click没有点击效果，原因不知，click.native试试[https://blog.csdn.net/yufengaotian/article/details/80509147](https://blog.csdn.net/yufengaotian/article/details/80509147)


如果使用router-link标签，加上@click事件，绑定的事件会无效因为：router-link的作用是单纯的路由跳转，会阻止click事件，你可以试试只用click不用native,事件是不会触发的。此时加上.native，才会触发事件。

题外话：
@ 这个东西实际上是 v-on 的简写，而 v-on 则是对 Vue 的事件体系封装后的 API 接口。

作者：WMLJS
链接：https://www.jianshu.com/p/bf5ede24c6e3
来源：简书
著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。

axios 代码没有执行，不执行说明有错误
居然不报错！！
官网的肯定行，但this undefined
axios的两种写法，
[Vue，使用axios中this为undefined解决，this指向](https://blog.csdn.net/m0_37885651/article/details/81558623)
也不是错误只是回调的时候对应

js；数组

```javascript

1）delete: 只是被删除的元素变成了 undefined 其他的元素的键值还是不变。

2) splice: 该方法会改变原始数组


pop():该方法用于删除数组的最后一个元素，并返回被删除的元素。官方语法：arrayObject.pop()

shift():该方法用于删除数组的第一个元素，并返回被删除的元素。官方语法：arrayObject.shift()

push():该方法用于向数组末尾添加一个或者多个元素，并返回新的长度。官方语
```
[vue循环创建id拼接索引](https://segmentfault.com/q/1010000017262603/a-1020000017263123)


报错 [Vue warn]: Avoid mutating a prop directly since the value will be overwritte

在vue2.0中子
[Avoid mutating a prop directly since the value will be overwritte
](https://juejin.im/post/5be4e50ae51d4537452913c7)


iview 中collapse的on chage 要用@ 不要参数

![在这里插入图片描述](http://img.yayi.site/csdn/20191229161932657.png-watermaskStyle)

==子组件声明接收一个props
那么父组件在return 中有这个属性，并在templete中声明，具体在哪，这是有讲究的，我的是在声明了子组件的标签才能 传过去，之前 死活传不去，，非标签如路由的过去的组件要在 routerview 标签中声明==
![在这里插入图片描述](http://img.yayi.site/csdn/20191229164220539.png-watermaskStyle)
![在这里插入图片描述](http://img.yayi.site/csdn/20191229164233836.png-watermaskStyle)
 
 webstorm alt 8 加上typeof 可以得到类型，深度太大的时候用。
了解一下正则表达式的贪婪模式
![在这里插入图片描述](http://img.yayi.site/csdn/20191229220346488.png-watermaskStyle)


不要用他默认table的selection,自己生成复选框，自己做选中，iview自己的多选有点鸡肋
this.$refs.mytable.$refs.tbody.clickCurrentRow(0)


mouted 中this 没有data的定义，用this.refresh 刷新才引用，原因未知
