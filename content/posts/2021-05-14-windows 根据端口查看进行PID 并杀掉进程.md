 首先用netstat -ano | find “端口号”查出进程号
2. takslist 查询当前的进行
3. . 如何杀死进程呢  tasklist /pid ${xx}


https://www.cnblogs.com/qianjinyan/p/10772540.html
发现不行呢，权限不够，用管理员权限运行cmd，发现又报错了，说要强制执行才可以，加上-F


