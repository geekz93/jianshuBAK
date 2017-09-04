local.cshrc local.login local.profile

这些文件是个模板
你可mv/cp 成你要的.profile .cshrc .login

当你添加用户时，这些文件是从/etc/skel 下面拷贝到你得用户目录下的。
.profile我知道是设置环境变量的
.cshrc .login有什么作用呢
不同的shell有着不同的配置文件
```
/etc/profile            $HOME/.profile  /bin/sh
/etc/profile            $HOME/.kshrc    /bin/ksh
/etc/.login             $HOME/.login    /bin/csh
```
