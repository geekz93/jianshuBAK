- 网卡名称: `ip a`
- 修改 `/etc/network/interface` 添加内容:
```
auto ens33 #网卡名称
iface ens33 inet static  #设置静态ip
address 192.168.145.135
netmask 255.255.255.0
getway  192.168.145.1
```
- 重启电脑: `reboot`
