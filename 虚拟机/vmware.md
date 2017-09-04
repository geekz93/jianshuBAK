- linux使用vmware挂载的镜像文件
linux实际上已经读到 iso 文件了，在 /dev/cdrom 中，手动进行挂载就能获取其中的内容了
```
mkdir /ISO
mount /dev/cdrom /ISO
```
