问题描述：
[操作系统](http://lib.csdn.net/base/operatingsystem)为RHEL6.5，安装时使用的是默认主机名localhost，后来不知道怎么，在没有人修改的情况下，重启后就变成了bogon。导致我们的[数据库](http://lib.csdn.net/base/mysql)等应用无法正常启动。在排除人为修改的原因后，检查了/etc/sysconfig/network等文件，发现里面HOSTNAME是localhost，并没有什么问题。后来经过联系红帽客服及在群里寻求帮助，当然 还有伟大的度娘和谷歌，终于算是基本搞明白了其中的原因。

成因分析：
[Linux](http://lib.csdn.net/base/linux)系统启动时，会经历BOIS自检，系统引导，启动内核，初始化系统这几步 ，其中初始化系统时，会依次执行/etc/rc.sysinit,/etc/rc.d/rc* 等脚本文件，其中在rc.sysinit有这样 一段代码

```
if [ "$HOSTNAME" = "localhost" -o "$HOSTNAME" = "localhost.localdomain" ]; then  
         ipaddr=$(ip addr show to 0.0.0.0/0 scope global | awk '/[[:space:]]inet / { print gensub("/.*","","g",$2) }')  
         for ip in $ipaddr ; do  
                 HOSTNAME=  
                 eval $(ipcalc -h $ip 2>/dev/null)  
                 [ -n "$HOSTNAME" ] && { hostname ${HOSTNAME} ; break; }  
         done  
 fi  
```
这段代码先判断了主机名，如果主机名是localhost或者localhost.localdomain，则获取主机IP地址并执行DNS逆向解析，将解析到的结果赋值给HOSTNAME。假设我主机IP为192.168.1.47，手动执行下列命令，得到的返回值为bogon。也就是莫名其妙出现的主机名

经查阅资料，了解到有些DNS服务器，会将私有地址，保留地址这样的不应该出现在网络上的IP地址解析成bogon
解决方法：

知道问题的原因了，解决起来也就容易了。

推荐的最佳解决方案，是修改主机名，只要主机名不是localhost或者localhost.localdomain，那么操作系统就不会执行DNS反向解析等操作，问题自然也不会出现。而且并不推荐使用默认主机名进行系统安装。具体操作就是修改/etc/sysconfig/network文件中HOSTNAME键值。

再有就是更改DNS域名服务器，有些域名服务器会对bogon进行过滤。多试试哪些行哪些不行。或者不给服务器配置DNS，大部分服务器其实是没有上网需求的。DNS服务器一般是在/etc/resolv文件中，有些也会写在/etc/sysconfg/network-scripts/ifcfg-eth0中。
