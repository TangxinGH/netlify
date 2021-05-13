# python django ajax

chrome 显示 failed to xxx 。以为ajax 数据量大。

1. 设置ajax 的timeout 没有用
2. 换firefox 网站不许 Firefox 显示被嵌入的网页 。哦。（firefox nb）
3. django 的官方 xframe_options_exempt [在view的视图方法上注解](https://docs.djangoproject.com/en/3.1/ref/clickjacking/)
4. ![在这里插入图片描述](http://img.yayi.site/csdn/20210406174917938.png-watermaskStyle)

5. ok.安全问题。

