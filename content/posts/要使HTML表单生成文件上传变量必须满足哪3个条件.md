必须使用POST方式提交(设置表单 method="post" )；(2) 必须设置表单enctype属性为  enctype="multipart/form-data" ；(3) 表单中要有一个文本域控件。


 application/x-www-form-urlencoded： 窗体数据被编码为名称/值对。这是标准的编码格式。
multipart/form-data： 窗体数据被编码为一条消息，页上的每个控件对应消息中的一个部分。
text/plain： 窗体数据以纯文本形式进行编码，其中不含任何控件或格式字符。 



[https://blog.csdn.net/mazhibinit/article/details/49667511](https://blog.csdn.net/mazhibinit/article/details/49667511)

post数据在body里，而不是协议头。
[https://www.cnblogs.com/biyeymyhjob/archive/2012/07/28/2612910.html](https://www.cnblogs.com/biyeymyhjob/archive/2012/07/28/2612910.html)
![在这里插入图片描述](http://img.yayi.site/csdn/20200602171731767.png-watermaskStyle)

chrome 浏览器的post 数据是 表单数据的能看到。上传文件就看不到body了了？不懂。可能浏览器优化了。fidder 抓到的到是与http协议一致。 firefox 是可以看到body的，选择参数。chrome 对于post 的body 。嗯，反正multipart/form-data 的是看不到？其它的是优化一下，显示出来可以看到（在header最后面）。但不属于headers

http协议：
一个HTTP请求报文由请求行（request line）、请求头部（header）、空行和请求数据4个部分组成
![在这里插入图片描述](http://img.yayi.site/csdn/20200602172740136.png-watermaskStyle)
请求数据应是body了吧。[＜request-body＞。
