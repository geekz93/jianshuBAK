## 列相加
ps 显示出来的结果
```
$ ps -efo pmem,rss|sort -r                          
%MEM  RSS
 2.3 2972792
 0.1 80680
 0.1 40872
 0.1 40872
```
- 查看内存占用百分比,将第一列相加:
```
ps -efo pmem,rss|awk '{sum += $1} END {print sum}'
```
- 查看内存占用大小,将第二列相加,除1024将KB缓存M
```
ps -efo pmem,rss|awk '{sum += $2} END {print sum/1024}'
```
