[toc]

==注：最后放弃了。太难搞了。== ~~浪费时间~~ 

### kali hard blocked yes
```c
0: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: yes
```

```bash
root@kali:/home/kali# airodump-ng wlan0mon
ioctl(SIOCSIFFLAGS) failed: Operation not possible due to RF-kill
Failed initializing wireless card(s): wlan0mon
```
不要用kali的安装版

kali 的话尽量用iso

### pandorabox opkg update unknown

```bash
[root@PandoraBox:/root]#opkg install aircrack-ng
Unknown package 'aircrack-ng'.

```

```bash
#opkg update
Downloading http://downloads.pangubox.com:6380/pandorabox/20.03/targets/ralink/mt7621/packages/Packages.gz
wget: server returned error: HTTP/1.1 404 Not Found
*** Failed to download the package list from http://downloads.pangubox.com:6380/pandorabox/20.03/targets/ralink/mt7621/packages/Packages.gz

Downloading http://downloads.pangubox.com:6380/pandorabox/20.03/packages/mipsel_1004kc_dsp/base/Packages.gz
wget: server returned error: HTTP/1.1 404 Not Foun
```
这个是opkg 的更新源还没有20.3版本的，改为19版的
/etc/opkg.conf
![在这里插入图片描述](http://img.yayi.site/csdn/20210206110723165.png-watermaskStyle)
[详细见https://qiedd.com/409.html](https://qiedd.com/409.html)


### kali wifiphisher
kali wifiphisher 钓鱼弹窗没有出现  Captive portal not popping up

1. apt-get install wifiphisher 源/etc/apt/source.list官方的源。因为之前装pycrt的时候换过源（源码 not found）。
2. wifiphisher --force-hostapd启动失败发现日志占用了8080 ，443  ，杀掉。
3. 弹不出页面。53 端口lsof -Pn +M | grep ':53 (LISTEN)'  查看dnsmap 。 [https://github.com/wifiphisher/wifiphisher/issues/1093](https://github.com/wifiphisher/wifiphisher/issues/1093)
4. 又看了下，kail 与wifiphisher 的ip地址是不是同一网段。同一网段会有冲突。然而并不是

最后，半天了，我reboot了一下。fuck 。 可以了！！！。我tm

### rt3070 openwrt
这个在openwrt 19.7中是适用的。在pandorabox中不适用，要烧录吧。
openwrt 直接安装kmod的usb包，还有rt2800一系统驱动 。然后重启。

### 用 extroot 为 openwrt 扩充存储空间
这个文章非常好
[用 extroot 为 openwrt 扩充存储空间](https://www.solarck.com/openwrt-extroot.html)

要安装程序的话，还是用pivot-root的方式。
只有一个usb的话。买个扩展器。
1. 安装包
2. 格式化u盘成ext
3. 挂载。建swap 
4. tar 移动文件。
5. vim fstab 
6. 不用u盘时，关机，再取出。

### fluxion 在ubuntu上。
最好添加kali源。因为很多包没有

### openwrt 挂载网络磁盘

读写权限。
setsebool -P samba_export_all_ro on
测试

 smbclient //127.0.0.1/yayi -U yayi
do_connect: Connection to 127.0.0.1 failed (Error NT_STATUS_CONNECTION_REFUSED)
0

I guess these issues are related to one of the updates that were released to fix the Badlock Bug. The full list of fixes are listed in Samba Security Releases and the announcements for each patch-set provides useful information on what has changed.

After upgrading my old CentOS 5 system, I had issues connecting Winbind to an AD domain controller and the clue to fixing them was in the announcement for CVE-2016-2115 – SMB client connections for IPC traffic are not integrity protected.

This documented the new smb.conf option, client ipc signing. While the documentation recommends explicitly setting this option to mandatory, I found that auto also solved those issues so I added the following line to my smb.conf (under the [global] section):

==client ipc signing = auto==
