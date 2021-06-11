SD卡缓存目录
当应用需要将图片或者文件缓存到SD卡中时要去申请创建目录，有下面几种途径 我们可以通过API调用应用专属目录:

// /storage/emulated/0/Android/data/app_package_name/files/Pictures
Content.getExternalFilesDir(Environment.DIRECTORY_PICTURES); 
// /storage/emulated/0/Android/data/app_package_name/cache
Content.getExternalCacheDir(); 
上面两个目录是专属于当前app的，当应用被删除时，上面目录下的文件也会清空
不需要权限
[https://juejin.im/entry/5951d0096fb9a06bb8745f75](https://juejin.im/entry/5951d0096fb9a06bb8745f75)


kotlin:[https://developer.android.com/training/permissions/requesting?hl=zh-cn](https://developer.android.com/training/permissions/requesting?hl=zh-cn)
关于权限的问题
![在这里插入图片描述](http://img.yayi.site/csdn/20200329160341919.png-watermaskStyle)
这个地方：![在这里插入图片描述](http://img.yayi.site/csdn/20200329160406708.png-watermaskStyle) arrayof
kotlin 简单原生的http请求：[https://www.jianshu.com/p/5eee1ef02700](https://www.jianshu.com/p/5eee1ef02700)

==android 的权限不是声明就行了的，还要在运行过程中动态弹出申请==华为的好像有始终允许这个选项，android p ?10?



基线：对齐 先show baseline 点住 并拖到你要对齐的另一个组件。
[https://developer.android.google.cn/training/basics/firstapp/building-ui](https://developer.android.google.cn/training/basics/firstapp/building-ui) 按照官方的学习就行，反正是中文的。
这里作一些重点标记：
1. 链是两个或多个视图之间的双向约束条件，可让您采用一致的方式安排链接的视图。
2. Match constraints”表示宽度将延长以符合水平约束条件和外边距的定义。因此，文本框将拉伸以填充去除按钮和所有外边距后剩余的水平空间。


---
grade impementation 是在build.grade中


---
还是去看官方文档吧
