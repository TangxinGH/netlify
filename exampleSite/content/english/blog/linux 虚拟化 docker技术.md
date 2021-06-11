linux 原本就有namesapce这一概念.

interl 提供了，，intel vt

---

### 进程隔离技术
1. chroot
	内核提供的一个系统调用 。访问文件系统目录的时候，限制了用户根目录。
	> https://lxr.missinglinkelectronics.com/linux/fs/open.c#L539
	源码位置： https://elixir.bootlin.com/linux/latest/A/ident/CHROOT

 539SYSCALL_DEFINE1(chroot, const char __user *, filename)
 540{
 541        return ksys_chroot(filename);
 542}

2.  namespace
	进程 独立命令空间。
	隔离功能有 UTS IPC PID NETWORD  mount user

3.  cgroup 
创立namespace之后，通过 cgroup对资源进行相关限制。
