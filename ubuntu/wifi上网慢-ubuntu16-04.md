原因未知
解决方法：在 `/etc/modprobe.d/iwlwifi.conf` 中添加
```
options iwlwifi 11n_disable=1
```
重启电脑
