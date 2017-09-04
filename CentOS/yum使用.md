## 配置源
- GPG key目录: `/etc/pki/rpm-gpg/`

yum 的repo在目录 `/etc/yum.repos.d/` 中, 后缀名为 repo
- **清除先前的repo缓存:** 
```
yum clean all # 清除之前的repo
```
- **下载repo文件(从帮助网页中找到repo文件下载), 至 `/etc/yum.repos.d/`目录:** 
  - 网易镜像: http://mirrors.163.com/
CentOS repo 文件: http://mirrors.163.com/.help/CentOS6-Base-163.repo
  - 阿里镜像: http://mirrors.aliyun.com/
CentOS repo 文件: http://mirrors.aliyun.com/repo/Centos-6.repo

- 修改下载的repo文件, 替换 `$releasever`
先在镜像页面中,找到有文件的目录, 如: 在网易镜像下的的 centos/6.9/有文件.将所有的 `$releasever` 替换为 `6.9`

- **下载repo到本地:** 
```
yum makecache # 下载repo中的数据库
```

- 设置 gpgcheck=0

## 使用
- 本地iso的repo文件
```
[localiso]
name=local
baseurl=file:///media/cdrom/
gpgcheck=1
gpgkey=file:///media/cdrom/RPM-GPG-KEY-CentOS-7
```

- 使用本地iso的repo安装
localiso是repo的名字，自定义的
```
yum --disablerepo=\* --enablerepo=localiso install gdb -y
```

- 查看安装了哪些内容
```
yum history info 15 
```

- 恢复安装前的状态
```
yum history list eclipse-pde   #查看id为 176
yum history undo 176  #回滚
```

- 只下载, 不安装
在 `/etc/yum.conf` 文件中指定  `cachedir=/home/zooo/packages`
```
 sudo yum install --downloadonly <package-name>  #指定目录
```

- 强制覆盖安装: 
```
rpm -ivh --force --nodeps httpd-2.2.3-91.el5.centos.i386.rpm
```
