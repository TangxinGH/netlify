```c
adb uninstall cn.edu.glut.llk&&adb install app-debug.apk&&adb shell am start -n cn.edu.glut.llk/cn.edu.glut.llk.MainActivity
```

> &&
> 

adb 局域网调试。首先手机手动开启端口。
方法一：==不需要root ，但需要数据线==，先数据线cmd开启 tcpip模式。相当于在手机上开启了端口。拨掉数据线，就可以了。==但手机重启后，得重新数据线一遍。==

方法二：root 权限开启tcpip模式。直接在手机上开启。百度命令。

