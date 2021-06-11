vscode latex workshop recipe terminated with fatal error spawn latexmk enoent

window + telive2020 

使用清华的在线安装。

telive 3.0G  几乎包含所有的包了。比如latexmk
搜索了一下，好像是环境变量路径问题。

textlive manager  搜索得到latexmk
cmd 输得出东西。
window的path 也是安装时自动配好的。

我尝试更改vscode 中的setting.json 的 workshop中的env 。没用。
在vscode中的终端，tex 却输不出东西。
看了下终端配置，没有问题。
重启vscode没有用。

哦，我三天前装的telive，三天没关过机了。。。。。重启，ok ,f**k!

话说，cmd 只有全部关闭再打开环境就可以生效了，vscode重启却做不到？？？
