## 文件命名
- 有多个目录,每个目录中有多个文件,不同目录中的文件名相同,如何合并这些目录
目录结构如图
![01](http://upload-images.jianshu.io/upload_images/3022282-d723e65ad8dfc5a8.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
  + 实现程序
```bash
#!/usr/bin/bash
# 统计文件数目
fcnt=$(find ./dir* -type f|wc -l)
# 根据文件数使用0占位
zero_len=${#fcnt}
# 使用printf补零
# printf "%02d" %i
# 字符串拼接使用 ${a}${b}
cnt=1
for i in $(find ./dir* -type f)
do
    newname=$(printf "%0"${zero_len}"d.f" $cnt)
    cp $i $newname
    echo "rename $i to $newname"
    cnt=$((cnt+1))
done
```

- 批量替换后缀: 
```
for i in *.bmp;do mv $i ${i/bmp/jpg}; done
```
