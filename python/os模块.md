- 执行 系统 命令：http://www.jb51.net/article/55327.htm
- os.system(cmd)
- os.linesep: 行终止符
- os.path.sep: 路径分割符
  * 路径测试: py3 输入反斜杠后系统会自动加入转义符, 新加的转义符不记录字符穿长度

## os
- 显示目录中的文件：`os.listdir()`
- 切换到指定目录：`os.chdir(path)`
- 创建目录：`os.mkdir(path)`
- 得到当前目录路径: `os.getcwd()`
- 打开当前目录: `os.startfile(os.getcwd())` 或者 `os.startfile('.')`，startfile既可以打开目录， 也可以打开文件

## os.path
- 得到文件大小：`os.path.getsize(filename)`
- 得到文件后缀：`(filename,extension) = os.path.splitext(tempfilename)`

目录操作：
os.mkdir("file")                   创建目录
复制文件：
shutil.copyfile("oldfile","newfile")       oldfile和newfile都只能是文件
shutil.copy("oldfile","newfile")            oldfile只能是文件夹，newfile可以是文件，也可以是目标目录
复制文件夹：
shutil.copytree("olddir","newdir")        olddir和newdir都只能是目录，且newdir必须不存在
重命名文件（目录）
os.rename("oldname","newname")       文件或目录都是使用这条命令
移动文件（目录）
shutil.move("oldpos","newpos")   
删除文件
os.remove("file")
删除目录
os.rmdir("dir")只能删除空目录
shutil.rmtree("dir")    空目录、有内容的目录都可以删
转换目录
os.chdir("path")   换路径
