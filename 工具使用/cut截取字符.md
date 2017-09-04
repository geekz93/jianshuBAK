- 以‘=’为分隔符，取第二列
```
var='path=/home/zabbix'
echo $var|cut -d "=" -f 2
```
