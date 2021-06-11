> pip install FileNotFoundError: [Errno 2] No such file or directory:

>WARNING: Retrying (Retry(total=4, connect=None, read=None, redirect=None, status=None))connection broken by

>timeout 

>proxy error

>after connection broken by 'ProxyError('Cannot connect to proxy.', FileNotFoundError(2, 'No such file or directory'))

>'ConnectTimeout 

#### 起因
如果你只是安装一个依赖，那换个方法就是了。但安装requirements。没有一种方法能安装成功。就很狗血了。
这种问题在哪种方法都可能出现 
#### pip 超时就设置长一点呗
pip install 的时候总是这样。不是超时（国内外网速的差异导致下载超时？？），就是代理错误，或者找不到。
设置--default-time-out 就不超时了。
### 代理问题，换个代理？或者换网络
我使用了代理。关掉代理就正常了。或者使用pycharm 的requirements插件安装，右击，requirements.txt中的文件依赖安装，好像这样==比命令行安装==会走代理（或者不会proxy error）
但是，慢！pip 容易断。我换到联通网，好像pip 它又行了。。。
于时使用镜像源。如清华的，douban的。-i https://pypi.douban.com/simple/
然而这种镜像，有时候，找不到包！！或者 不满足条件 ！
### conda 并不是那么好。
于是，我使用了conda ，但这个安装单个包，还行，安装requirements.txt
会找不包，中断。fu**。不是说conda好装包吗？window下又用不了脚本。

回到pip ,换个代理，不行，根本没连上代理，error
#### 分而治之吧
用conda 安装大部分先，再解决剩余的。
[Stop pip from failing on single package when installing with requirements.txt](https://stackoverflow.com/questions/22250483/stop-pip-from-failing-on-single-package-when-installing-with-requirements-txt)
https://blog.csdn.net/Mao_Jonah/article/details/89502380
他这里的while read requirement; do conda install --yes $requirement || pip install $requirement; done < requirements.txt
是linux的.

这里有个window的
 

```python
# This code install line by line a list of pip package
import os
import sys
from pip._internal import main as pip_main


def install(package):
    os.system('conda install --yes '+package)
    # pip_main(['install', package])


if __name__ == '__main__':
    with open(sys.argv[1]) as f:
        for line in f:
            install(line)
```

python xx.py requirements.txt　先解决掉大部分。我的是在pycharm的terminal中运行的。你conda 没有环境变量的话，到 anaconda的env中运行吧。

然后　使用－ｉ　豆瓣源。或者pip 安装个别的。

本来写个bat的，不会

```bash
@echo off

set targe=''
setlocal enabledelayedexpansion
for /f   %%i in (requirements.txt)  do (
set target=%%i
conda install --yes !target!
)

pause

conda install --yes --file requirements.txt
if %errorlevel% == 0 （


  ）else(

  )
```
#### 小技巧
> 还有anaconda 弄多几个channels 。目前有清华的和sjtug，bfsu
![在这里插入图片描述](http://img.yayi.site/csdn/20210125210739189.png-watermaskStyle)
用户目录下配置文件
ssl_verify: true 这是什么
channels:
  - https://mirrors.bfsu.edu.cn/anaconda/pkgs/main
  - https://anaconda.mirrors.sjtug.sjtu.edu.cn/pkgs/main
  - https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/main
  - defaults


### 总结
总的来说，==没有一个能用的==  代理问题，网速问题，找不到问题。
pip 是除了网速外，比较全的。
==只能先解决大部分依赖吧==。再解决小部分的。
用脚本pip -i https解决跳过错误，也是同样的道理。
话说，pip 安装有跳过错误的依赖安装吗？

ssl 问题 pip -trusted-host=
或者-i https http 变成https


### 补充
找不到满足的包，其实可能是版本与python 版本不合适，比如2.7 和3.8 。32位与64位。还有tensorflow 还跟cpu有关gpu有关。所以经常 不满足条件 。这个去掉版本号就行了。像pandas这种和cpu有关的指定版本不好。

还是pip 安装比较好。

#### pycharm requirements插件
这个他未安装和升级都会有标黄，难以区分，
![在这里插入图片描述](http://img.yayi.site/csdn/20210126152223614.png-watermaskStyle)
点击警告
![在这里插入图片描述](http://img.yayi.site/csdn/20210126152251349.png-watermaskStyle)

直接选中窗口，打字，搜索 ![在这里插入图片描述](http://img.yayi.site/csdn/20210126152327906.png-watermaskStyle)

### 安装未安装的包。
有时候，requirements.txt 全是等于号。我不想降级安装已经安装的包。这时候搜索替换

![在这里插入图片描述](http://img.yayi.site/csdn/20210126154921844.png-watermaskStyle)
然后

```python
# This code install line by line a list of pip package
import os
import sys
from pip._internal import main as pip_main


def install(package):
    # os.system('conda install --yes '+package)
    pip_main(['install', package])


if __name__ == '__main__':
    with open(sys.argv[1]) as f:
        for line in f:
            install(line)

```
 局部安装

# tap代理
2021.3.15号补充
使用clash的tap模式，在网卡上代理

安装tap模式
关闭系统代理，
流量还是会走代理tap

不走系统代理，而是走网卡代理，tap模式，可以避免一些 pip 代理错误 

==之前的错误ARNING: Retrying (Retry(total=4, connect=None, read=None, redirect=None, status=None))connection broken by，是因为我开了tap网卡代理模式的同时，还开了system proxy 所以导致了这个问题==，不过也只有pip有这个问题，其他的软件 都能正常使用。tap应该是网络层透明，解决一些不走系统代理的问题

yaml文件
```yaml
#tap模式 https://docs.cfw.lbyczf.com/contents/tap.html
dns:
   enable: true
   enhanced-mode: redir-host # 或 fake-ip
   listen: 0.0.0.0:53
   nameserver:
      - 223.5.5.5
```

pip 安装 ：douban代理：

```bash
pip install -i  https://pypi.doubanio.com/simple/  --trusted-host pypi.doubanio.com   -r requirements.txt

```
有错误的话，先注释掉，安装大部分的先。

# tourch
这个要根据系统来的，不是这样安的，去官网下载 [添加链接描述](https://pytorch.org/get-started/locally/)

```bash
pip install torch==0.4.1 -f https://download.pytorch.org/whl/torch_stable.html
```
![在这里插入图片描述](http://img.yayi.site/csdn/20210315201236118.png-watermaskStyle)


