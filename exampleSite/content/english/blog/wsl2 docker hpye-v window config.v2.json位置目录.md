# docker desktop
window 现在的是wls2 方式。而不是hpye-v模式。

hpye-v有资源控制方式。没什么用。
wls   可以打开文件管理器。 expolre.exe 

wsl 语法：
wsl空格 linux命令

# du df ls -lh区别

备份的时候发现在，目录大小才几k，一直以为备份没成功。原来是ls 显示文件大小。linux 是inodo block方式存储的。ls 目录是目录inode大小。不是block内容，档案大小。
du -u 是所点磁盘大小。
df 是百分比。
百度。

# docker desktop目录在哪里
win>hype-v>wsl >linux>docker

所以要进linux里面
wsl enter
you can see  that 
![在这里插入图片描述](http://img.yayi.site/csdn/20210331192140416.png-watermaskStyle)

前面的是 用户名：默认发行版。

/目录是linux
/tmp/docker-desktop-root是docker 下的

![在这里插入图片描述](http://img.yayi.site/csdn/2021033119234585.png-watermaskStyle)
又一个linux 

没找到。
去微软官网有
github下面有讨论
https://blog.csdn.net/qqhappy8/article/details/106819429

---
\\wsl$\docker-desktop
![在这里插入图片描述](http://img.yayi.site/csdn/20210402110530864.png-watermaskStyle)

我这里是位于网络位置
![在这里插入图片描述](http://img.yayi.site/csdn/20210402110601105.png-watermaskStyle)

# 搜索 容器id
![在这里插入图片描述](http://img.yayi.site/csdn/20210402111027147.png-watermaskStyle)
![在这里插入图片描述](http://img.yayi.site/csdn/20210402111637857.png-watermaskStyle)


\\wsl$\docker-desktop-data\version-pack-data\community\docker\containers\d4f7e58b82309b6b393ab006b050dcf626701c73dd2c92bf3f81d31c65afffdf

![在这里插入图片描述](http://img.yayi.site/csdn/20210402112135104.png-watermaskStyle)
两个，默认的是docker-desktop 。cmd下 打 wsl 进来 的也是docker-desktop，所以是找不到容器的配置文件的。

![在这里插入图片描述](http://img.yayi.site/csdn/20210402112249120.png-watermaskStyle)

