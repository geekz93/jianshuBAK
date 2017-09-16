> http://www.thegeekstuff.com/2012/04/curl-examples/
> http://www.cnblogs.com/gbyukg/p/3326825.html

下载单个文件，默认将输出打印到标准输出中(STDOUT)中
```
curl http://www.centos.org
```

通过-o/-O选项保存下载的文件到指定的文件中：
-o：将文件保存为命令行中指定的文件名的文件中
-O：使用URL中默认的文件名保存文件到本地
```
1 # 将文件下载到本地并命名为mygettext.html
2 curl -o mygettext.html http://www.gnu.org/software/gettext/manual/gettext.html
3 
4 # 将文件保存到本地并命名为gettext.html
5 curl -O http://www.gnu.org/software/gettext/manual/gettext.html
```
