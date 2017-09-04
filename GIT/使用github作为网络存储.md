## 初始化git仓库
**流程:** `1.安装git -> 2.配置git(直接运行程序) -> 3.在github中新建repo -> 4.将本地文件夹和repo关联,并上传文件到repo中 `

1. **安装git工具:** 
安装压缩包中的git工具,全部按照默认设置，一路next

![git工具](http://upload-images.jianshu.io/upload_images/3022282-b6fcdb3feb6768f8.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

2. **配置git:**  
右键 -> gitbash -> 输入 `./git_set.sh` 回车

![配置git](http://upload-images.jianshu.io/upload_images/3022282-404f4c141fe379e6.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![](http://upload-images.jianshu.io/upload_images/3022282-bb4d00b01ac4d8ed.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

3. **在github中新建repo:** 
```
地址: https://github.com/geekz93/
密码: ****
```

点击页面右上角的`+`号 -> New repository
![create repository1](http://upload-images.jianshu.io/upload_images/3022282-995edd37b746ec55.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

输入repo的名称后,点击create repository
![create repository2](http://upload-images.jianshu.io/upload_images/3022282-f1c7b77c48b2dc0b.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

先不要关闭页面,这个repo的地址,后面会用到
![create repository3](http://upload-images.jianshu.io/upload_images/3022282-8d6558940778f078.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

4. **关联本地目录:** 
    - 将 `git.sh 和 .gitignore`文件拷贝到要关联到repo的目录中,我这里把**金属样本**这个目录和上面创建的`iron_images`目录关联
![copy files](http://upload-images.jianshu.io/upload_images/3022282-555f8526fde1f5bd.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

    - 在**金属样本**目录的空白处右键,点击`git bash here`,输入 `./git.sh init` 要输入repo的地址,把上面说的repo地址复制粘贴进去,回车即可
![initial](http://upload-images.jianshu.io/upload_images/3022282-f8e194376350c14d.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

    - 上传文件到repo中, 输入 `./git.sh upload` 看到 `writing...done`表示上传完成,这时刷新之前的网页就可以看到上传的文件了~~
![upload](http://upload-images.jianshu.io/upload_images/3022282-17d3264d1e2bb7f7.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![images in github](http://upload-images.jianshu.io/upload_images/3022282-55b3a798fd069f25.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)



## 在令一台电脑中配置git
在另一台电脑中安装git工具,配置git,和上面步骤1,2一样操作.
配置好git后,新建一个目录,把压缩包中的: `git.sh` 和 `.gitignore`文件拷贝到这个目录里
![new directory](http://upload-images.jianshu.io/upload_images/3022282-d536615009683b36.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
进入gitbash后输入`./git.sh init`进行初始化(和repo关联), repo的地址可以在网页中看到
![repo site](http://upload-images.jianshu.io/upload_images/3022282-45d741e4751139b8.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

关联完成后在bash中输入`./git.sh download` 就可以下载repo中的文件了
![下载完成了^_^](http://upload-images.jianshu.io/upload_images/3022282-730e38ba3644abd5.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

## 日常使用
完成上面的配置后,日常使用就非常简单了: 过程如图所示

![公司和家里的电脑同步文件](http://upload-images.jianshu.io/upload_images/3022282-ce6929f0fb8eb79b.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

两台电脑都的**金属样本**目录都和github上的**iron_images**目录关联了.在公司的电脑里往**金属样本**目录里添加东西后,使用
```
./git.sh upload
```
上传到github上
回家后**进入金属样本目录**使用
```
./git.sh download
```
下载github上的新内容, 同样在家里工作完了, 新增加的内容也可以upload到github上, 到工作再download下来接着做
