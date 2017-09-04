## option
```
-i: ignore case distinction 忽略大小写
-I: 忽略二进制文件
-r/-R: 递归搜索, --exclude=*.exe 忽略exe后缀文件,  --exclude-dir=linux* 忽略linux开头的目录
-n: 行号
-v: 显示不匹配行
-o: 只显示找到的关键字, 而不显示整行
```

## 应用
 - 搜索简书中的笔记: 
找和 netstat 有关的笔记, 并显示行号: `grep -irn "netstat"`

- 或关系: 
`grep -E "#|^$"
