vm要桥接模式。

两台机子ping不通：中间是否有路由器或者防火墙。

机子上的防火墙：要关掉，
![在这里插入图片描述](http://img.yayi.site/csdn/20200319120427434.png-watermaskStyle)
使用中的字样
ping是ip协议中的ICMP包，在入站规则中可以看到：
![在这里插入图片描述](http://img.yayi.site/csdn/20200319120538878.png-watermaskStyle)
![在这里插入图片描述](http://img.yayi.site/csdn/2020031912055033.png-watermaskStyle)
绿色表示通过。

单向ping得通的话有可能是一台机子有防火墙。
