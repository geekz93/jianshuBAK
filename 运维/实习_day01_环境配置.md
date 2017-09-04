## DAY-1 环境配置
- 设置局域网代理：将外部网络进行一次过滤
    * 过程: internet选项 -> 连接 -> 局域网设置 -> 地址:proxy.asiainfo.com 端口:8080 -> 高级(设置不使用代理的地址): `10.*.*.*;172.*.*.*;*asiainfo*;221.*.*.*`

- 帐号:
    * 测试域vpn：duyulu/237b7Jkg MAC: F0DEF10F014F(mac地址有什么用?)
    > - 测试域的作用：每个主机存在一个作用域中，因此在登录主机的时候需要让自己的电脑和要登录的主机处在同一个作用域，通过登录 vpn 实现
    > - 为什么要修改 MAC 地址

    * svn: wangzhou/wangzhou
    * jira: wangzhou/wangzhou
    * qq群: 261630697

- 设置邮件签名:

- SVN 客户端的使用:
    * 检出(从 svn 仓库下载): 新建目录 -> 右键, 然后选择 SVN checkout, 输入地址, 检出. 或者 右键菜单中选择 tortoiseSVN 浏览仓库, 再选择要下载的目录进行检出
    * update:
    * commit:

- JIRA 系统:
    * 任务领取, 跟进, 网址:http://10.12.2.234:8080/secure/Dashboard.jspa

- SecureCRT 使用:
    * 通过 ssh 登录主机: 在测试域中连接主机:10.248.12.31 和 10.248.12.35, 用户: dmonitor, 密码: dmonitor
    * 配置目录：C:\Users\zooo\AppData\Roaming\VanDyke\Config\Sessions\

- Oracle Client 和 pl/sql:
    * oracle client 用于连接 Oracle Server
    * plsql 是对 oracle client 中函数的封装, 登录格式: user/passwd@db
    * 配置 pl/sql: 
        1. tools -> preference -> 登录历史 -> 在固定用户中贴入历史用户
        2. 在路径: oracle\product\10.2.0\client_1\NETWORK\ADMIN\ 下设置配置文件: tnsnames.ora(该文件设置了要登录的 db 的相关参数)
    * 测试库是 nmctest 和 nmcdesign

- FileZilla使用:
    * 登录: 登录的账户需要有访问目录, 文件的权限
    * 下载: 在下载文件时, 需要选择本地路径, 如果没有选择本地路径则无法下载

- 连接打印机:
    * 控制面板 -> 设备和打印机 -> 右键,添加打印机 -> 添加网络打印机 -> 添加不再列表中的打印机, 输入打印机地址 -> 选择对应型号安装驱动

- 使用svn：第一次检出要输入账户，密码, 使用 tortoiseSVN 查看库中的数据，可以在里面选择再 checkout

- JIRA系统：任务系统，领取任务，记录任务完成情况，进度

- oracle_client/plsql: client 客户机，用于连接服务器，可以使用client直接命令行查找数据库，plsql，是对 oracle_client 函数的集成，可以使数据可视化，二者本质上是没有区别，使用plsql 更为方便
    * 基目录即 home

- plsql登录设置：
    1. 设置登录历史: user/passwd@db
    2. 替换 oracle/network/admin 目录中的 tnsnames 文件

- secureCRT
    - 登录之前需要先登录测试域
    - 登录：用户名和密码都为：dmonitor
