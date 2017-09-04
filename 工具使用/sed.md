## 用法
http://www.gnu.org/software/sed/manual/sed.html

## 例子
- string.txt
```
book--books--book--book--books
```

- **替换book为books, book后有s的不进行替换**
```
sed 's/book[^s]/books/' string.txt  # 后面无 g 每行第一个匹配
sed 's/book[^s]/books/g' string.txt # 替换行中所有匹配到的子串
sed 's/book[^s]/books/2g' string.txt   # 加数字表示从第几个匹配后开始替换接下来的
sed -i 's/book[^s]/books/g' string.txt # 直接修改文件
```

- 替换整行：
```
 sed 's/^[[:space:]]*line1$/aaa/g' ifcfg-ens33 #[[:space:]] 去除开头的空白
```

- **在最后一行插入文字:** 
需要文件中至少有一行
```
sed -i '$a\MaxStartups 1000' /etc/ssh/sshd_config
```
- 在指定行插入文字：
```
sed '2i\  line' ifcfg-ens33 # 2i\ 表示在第二行插入
```

- 删除空行：
```
sed '/^[[:space:]]*$/d' ifcfg-ens33
```

- 删除指定行：
```
sed "1,2d" file
sed "$num d" file #接受变量
```
