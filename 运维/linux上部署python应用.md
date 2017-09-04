## 软件包包括的目录
- 二进制文件路径:/bin,/sbin,(启动必须) /usr/bin ,/usr/sbin(运行必须)   /usr/local/bin ,/usr/local/sbin (第三方软件)
- 配置文件路径:/etc  ,/usr/local/etc
- 库文件路径: /lib ,/usr/lib ,/usr/local/lib , /usr/X11/lib
- 帮助文件路径: /usr/share/doc  ,/usr/share/man

## 部署思路
- 将最小系统的这些目录备份
- 安装完一个应用后, 将这些目录中不同的部分移动到自己新建的目录下
- 设置环境变量指向自己新建的目录

## 实现记录
- 使用 tar 得到原系统 `/bin /sbin /usr /lib /lib64 /etc` 目录的 tar 包并建立 snap
- 将原 snap 拷贝一份, 使用 tar -g snap 增量备份
- 将新增的文件移除
