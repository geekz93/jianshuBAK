- 例子： 生成一个大小为8G的文件
```
dd if=/dev/zero of=F8G count=8 bs=1G
```
原理：将由bs指定的1G大小的zero读入内存，然后分写入count指定的8*1G内容到文件
