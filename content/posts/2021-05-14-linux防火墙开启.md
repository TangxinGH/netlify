[https://www.cnblogs.com/yizhipanghu/p/11171211.html](https://www.cnblogs.com/yizhipanghu/p/11171211.html)
安装的服务器 用curl 试试在本地是否能打开，外网打不开时，可能防火墙原理
然后重启防火墙

iptables:
[https://blog.csdn.net/dhjibk/article/details/80633776](https://blog.csdn.net/dhjibk/article/details/80633776)
防火墙（firewalld与iptables）firewalld较新[https://blog.csdn.net/weixin_40658000/article/details/78708375](https://blog.csdn.net/weixin_33935777/article/details/91939964)

==宁愿关闭防火墙也不要卸载防火墙 ！！！== 机子会死

windows系统中 tomcat运行项目 其中

System.getProperty("user.dir") 输出的位置是当前tomcat所在的位置的bin目录
linux 

System.getProperty("user.dir")输出的位置是当前tomcat所在位置webapps目录里

————————————————
版权声明：本文为CSDN博主「wwq_vracle」的原创文章，遵循 CC 4.0 BY-SA 版权协议，转载请附上原文出处链接及本声明。
原文链接：https://blog.csdn.net/wwq_vracle/article/details/81774208


反正我用的是Thread.currentThread().getContextClassLoader().getResource("").getPath(); 这个肯定在类文件下面




 # Sets the default security model of the Apache2 HTTPD server. It does
    # not allow access to the root filesystem outside of /usr/share and /var/www.               # 看见这句话没有 //这句话说以下设置禁止了其他的根目录
    # The former is used by web applications packaged in Debian,
    # the latter may be used for local directories served by the web server. If
    # your system is serving content from a sub-directory in /srv you must allow
    # access here, or in any related virtual host.
    <Directory />
        Options FollowSymLinks
        AllowOverride None
            Require all denied
    </Directory>





DocumentRoot:"${SRVROOT}/htdocs/tp5/public/"  
