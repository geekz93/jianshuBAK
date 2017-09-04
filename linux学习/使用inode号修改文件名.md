```
ls -li # 查看inode号
#33584719 -rw-r--r--. 1 root root    5 Aug 30 02:40 a?ile
 find -inum 33584719 -exec mv {} afile \; # 使用find修改
```

