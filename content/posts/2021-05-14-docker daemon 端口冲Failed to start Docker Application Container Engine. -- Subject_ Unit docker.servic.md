Failed to start Docker Application Container Engine.
-- Subject: Unit docker.service has failed
-- Defined-By: systemd
-- Support: http://lists.freedesktop.org/mailman/listinfo/systemd-devel
--
-- Unit docker.service has failed.
--
-- The result is failed.

---
原因有很多
我的是这样的：
我stop 了其它的容器，新建了一个容器，用了一端口，而没注意到这个端口与其它容器端口是一样的，

后来，我要修改端口映射，去container目录下改hostconfig 之前 ，停止了docker 服务。

改了之后，启动服务。
由于之前的容器，是restart=always 。所以启动的时候，那两个冲突容器也启动了。所以失败。

**解决：**
备份，~~》删除 。~~ 
logs没有什么信息systemctl status docker  journalctl -xe也没有什么信息

docker ps 卡住，？？？好像是启动了，但。。。
 ==使用dockerd==
 
failed to start daemon: pid file found, ensure docker is not running or delete /var/run/docker.pid

有进程了？》删除 kill -9 pid
再dockerd 
 Error (Unable to complete atomic operation, key modified) deleting object [endpoint d14ea1a4 
 无法原子操作。
docker ps有东西了。
start 冲突的容器。出现了bind: address already in use。。结下来，要么删除容器，要么，再去改hostconifg来一遍。
