- 配置文件：/etc/sysconfig/network-scripts/ifcfg-网卡名
- 重启网络：service network restart

- 参数说明
    * device: 设备名称
    * hwaddr：网卡的序列号
    * type：
    * uuid：
    * onboot：是否启用设备
    * nm_controlled:
    * bootproto: 设置为 dhcp 动态分配ip
    * ipaddr: 静态 ip 地址
    * gateway：网关
    * prefix: 端口


- 动态 IP 配置参数
```
DEVICE=eth0
HWADDR=00:0C:29:5C:25:ED
TYPE=Ethernet
UUID=b3134434-73c8-4f63-8105-a8b59694179b
ONBOOT=yes
NM_CONTROLLED=yes
BOOTPROTO=dhcp
```

- 静态 IP 配置参数
```
DEVICE=eth0
HWADDR=00:0C:29:5C:25:ED
TYPE=Ethernet
UUID=b3134434-73c8-4f63-8105-a8b59694179b
ONBOOT=yes
NM_CONTROLLED=yes
BOOTPROTO=none
IPADDR=192.168.234.188
PREFIX=24
GATEWAY=192.168.234.1
```

- BUG:
设置为静态 IP 后无法连接外网
