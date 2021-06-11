pip 安装第三方库
第三方库：https://pypi.org/
[https://blog.csdn.net/lzqg1990/article/details/87877048](https://blog.csdn.net/lzqg1990/article/details/87877048)
在安装目录下 pip install xxx
[https://www.cnblogs.com/fengff/p/11804465.html](https://www.cnblogs.com/fengff/p/11804465.html)

关于脚本第一行的 #!/usr/bin/python 的解释，相信很多不熟悉 Linux 系统的同学需要普及这个知识，脚本语言的第一行，只对 Linux/Unix 用户适用，用来指定本脚本用什么解释器来执行。

有这句的，加上执行权限后，可以直接用 ./ 执行，不然会出错，因为找不到 python 解释器。

#!/usr/bin/python 是告诉操作系统执行这个脚本的时候，调用 /usr/bin 下的 python 解释器。

#!/usr/bin/env python 这种用法是为了防止操作系统用户没有将 python 装在默认的 /usr/bin 路径里。当系统看到这一行的时候，首先会到 env 设置里查找 python 的安装路径，再调用对应路径下的解释器程序完成操作。

#!/usr/bin/python 相当于写死了 python 路径。

#!/usr/bin/env python 会去环境设置寻找 python 目录，可以增强代码的可移植性，推荐这种写法。

分成两种情况：

（1）如果调用 python 脚本时，使用:

python script.py 

#!/usr/bin/python 被忽略，等同于注释

（2）如果调用python脚本时，使用:

./script.py 

#!/usr/bin/python 指定解释器的路径

PS：shell 脚本中在第一行也有类似的声明。

输出格式美化

Python两种输出值的方式: 表达式语句和 print() 函数。

第三种方式是使用文件对象的 write() 方法，标准输出文件可以用 sys.stdout 引用。

如果你希望输出的形式更加多样，可以使用 str.format() 函数来格式化输出值。

如果你希望将输出的值转成字符串，可以使用 repr() 或 str() 函数来实现。

    str()： 函数返回一个用户易读的表达形式。
    repr()： 产生一个解释器易读的表达形式。
Scarapy 爬虫框架。scrapy startproject module module 为模块名
![在这里插入图片描述](http://img.yayi.site/csdn/20200209204632509.png-watermaskStyle)
[https://www.runoob.com/w3cnote/scrapy-detail.html](https://www.runoob.com/w3cnote/scrapy-detail.html)



    Scrapy Engine(引擎): 负责Spider、ItemPipeline、Downloader、Scheduler中间的通讯，信号、数据传递等。

    Scheduler(调度器): 它负责接受引擎发送过来的Request请求，并按照一定的方式进行整理排列，入队，当引擎需要时，交还给引擎。

    Downloader（下载器）：负责下载Scrapy Engine(引擎)发送的所有Requests请求，并将其获取到的Responses交还给Scrapy Engine(引擎)，由引擎交给Spider来处理，

    Spider（爬虫）：它负责处理所有Responses,从中分析提取数据，获取Item字段需要的数据，并将需要跟进的URL提交给引擎，再次进入Scheduler(调度器).

    Item Pipeline(管道)：它负责处理Spider中获取到的Item，并进行进行后期处理（详细分析、过滤、存储等）的地方。

    Downloader Middlewares（下载中间件）：你可以当作是一个可以自定义扩展下载功能的组件。

    Spider Middlewares（Spider中间件）：你可以理解为是一个可以自定扩展和操作引擎和Spider中间通信的功能组件（比如进入Spider的Responses;和从Spider出去的Requests）

Scrapy的运作流程

代码写好，程序开始运行...

    1 引擎：Hi！Spider, 你要处理哪一个网站？
    2 Spider：老大要我处理xxxx.com。
    3 引擎：你把第一个需要处理的URL给我吧。
    4 Spider：给你，第一个URL是xxxxxxx.com。
    5 引擎：Hi！调度器，我这有request请求你帮我排序入队一下。
    6 调度器：好的，正在处理你等一下。
    7 引擎：Hi！调度器，把你处理好的request请求给我。
    8 调度器：给你，这是我处理好的request
    9 引擎：Hi！下载器，你按照老大的下载中间件的设置帮我下载一下这个request请求
    10 下载器：好的！给你，这是下载好的东西。（如果失败：sorry，这个request下载失败了。然后引擎告诉调度器，这个request下载失败了，你记录一下，我们待会儿再下载）
    11 引擎：Hi！Spider，这是下载好的东西，并且已经按照老大的下载中间件处理过了，你自己处理一下（注意！这儿responses默认是交给def parse()这个函数处理的）
    12 Spider：（处理完毕数据之后对于需要跟进的URL），Hi！引擎，我这里有两个结果，这个是我需要跟进的URL，还有这个是我获取到的Item数据。
    13 引擎：Hi ！管道 我这儿有个item你帮我处理一下！调度器！这是需要跟进URL你帮我处理下。然后从第四步开始循环，直到获取完老大需要全部信息。
    14 管道调度器：好的，现在就做！ 

注意！只有当调度器中不存在任何request了，整个程序才会停止，（也就是说，对于下载失败的URL，Scrapy也会重新下载。）
切换到模块下！命令行运行 python3 -m scrapy crawl quotes
crawl 是爬行的意思 
python -m 和 python 直接运行的区别：
[
https://www.cnblogs.com/xueweihan/p/5118222.html](https://www.cnblogs.com/xueweihan/p/5118222.html)
cmd 清屏命令cls


 # self
    # 代表类的实例，self
    # 在定义类的方法时是必须有的，虽然在调用时不必传入相应的参数。
    '类的帮助信息'  # 类文档字符串
    class 派生类名(基类名)
    ...

微信文章攫取：
[https://mp.weixin.qq.com/s/C92OHAVl6h0NwHGzX5-IIg](https://mp.weixin.qq.com/s/C92OHAVl6h0NwHGzX5-IIg)


Ide pycharm 
使用技巧：
因为其它人的项目与版本不一样，安装非常麻烦，可以new 一个虚拟环境，或者docker 或者ssh 使用其它的虚拟环境。了解一下。
![在这里插入图片描述](http://img.yayi.site/csdn/20200213140607184.png-watermaskStyle)

```bash
docker run  -v /file:/usr/src/file  -w /usr/src/file python:3.5 python  pyth.py
注意事项：
-v 将主机的py文件目录挂载到容器中的/usr/src/file
-w 指定容器的/usr/src/file目录为工作目录
python pyth.py 用容器中的python命令来执行工作目录的pyth.py
————————————————
版权声明：本文为CSDN博主「谦190」的原创文章，遵循 CC 4.0 BY-SA 版权协议，转载请附上原文出处链接及本声明。
原文链接：https://blog.csdn.net/u013355826/article/details/79963334
```
==python pyth.py是要执行的命令。docker ps -a 查看所有的容器，可以看到就是自己输入的commnd==

centos yum 配置，首先去官方的镜像网找一下，看一下官方的配置方法，因为有些是旧的博客。
[https://mirrors.tuna.tsinghua.edu.cn/help/centos/](https://mirrors.tuna.tsinghua.edu.cn/help/centos/)

==虽然putty很好用，但记不住密码这点==
idea jetbrains类的有ssh工具，[https://blog.csdn.net/Yafult/article/details/100881647](https://blog.csdn.net/Yafult/article/details/100881647)
7、将docker设置为开机启动(防止在重启系统后还需要手动执行命令启动docker)，执行命令：

systemctl enable docker

启动是 sytemctl start docker

远程访问(防火墙)
[https://blog.csdn.net/boling_cavalry/article/details/100049996](https://blog.csdn.net/boling_cavalry/article/details/100049996)

[https://zhuanlan.zhihu.com/p/52827335](https://zhuanlan.zhihu.com/p/52827335) 以一个镜像为基础进行自定义创建容器 
/bin/bash是进入？？容器内？
这个应该是用docker 创建一个python 环境，然后pycharm进入（连接到这个容器）远程运行？
==按照上面知乎的配置ssh ，出现access deny 不允许root登录，我下载vim（居然没有vi）看了ssh的配置中，没有变化 ，我重新配置了ssh.==
![在这里插入图片描述](http://img.yayi.site/csdn/20200213202819626.png-watermaskStyle)
[https://blog.csdn.net/ambm29/article/details/96483086](https://blog.csdn.net/ambm29/article/details/96483086)

### pip 镜像

（1）临时使用：
可以在使用pip的时候，加上参数-i和镜像地址(如
https://pypi.tuna.tsinghua.edu.cn/simple)，
例如：pip install -i https://pypi.tuna.tsinghua.edu.cn/simple pandas，这样就会从清华镜像安装pandas库。
————————————————
版权声明：本文为CSDN博主「Chaser_LittleBee」的原创文章，遵循 CC 4.0 BY-SA 版权协议，转载请附上原文出处链接及本声明。
原文链接：[https://blog.csdn.net/sinat_21591675/article/details/82770360](https://blog.csdn.net/sinat_21591675/article/details/82770360)

==Debian安装与启用sudo命令==
Debian默认是没有的？？

刚安装好的Debian9默认还没有sudo功能。

1. 先进入root用户，调用下面的命令后，输入密码

    $su

2. 安装sudo

    # apt-get install sudo

mogodb:
docker 
一开始是没有密码的，先加管理员帐号，admin 
有些角色只能是roles name 只能是管理员用，普通用户不行，。
在管理员帐号下创建其它的用户，如下例
![在这里插入图片描述](http://img.yayi.site/csdn/20200214225641414.png-watermaskStyle)
在管理员下创建其它用户有一个问题：
not authorized on admin to execute command：
[https://blog.csdn.net/chongke5244/article/details/100736604](https://blog.csdn.net/chongke5244/article/details/100736604)

两个鼠标 vmamre 可以用于虚拟机usb，没什么意义



docker 镜像配置[https://www.cnblogs.com/reasonzzy/p/11127359.html](https://www.cnblogs.com/reasonzzy/p/11127359.html)
通过 docker info 来查阅当前注册的镜像源列表，验证我们配置的镜像源是否生效

sudo docker info

oracle docker :
[https://blog.csdn.net/qq_38380025/article/details/80647620?utm_source=distribute.pc_relevant.none-task](https://blog.csdn.net/qq_38380025/article/details/80647620?utm_source=distribute.pc_relevant.none-task)
