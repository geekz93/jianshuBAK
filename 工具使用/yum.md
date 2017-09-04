CentOS7 yum
- **下载到本地:** 
  * 修改yum.conf: cachedir=/home/zabbix/yumZabbix
  * yum install --downloadonly php -y
  * 直接使用缓存进行安装: `yum -C install httpd`
- **撤销安装, 删除依赖:** 
  `yum history undo id`
