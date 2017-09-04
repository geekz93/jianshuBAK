## 1 PSNR 的不足
峰值信噪比（PSNR）是均方差（MSE）的单调函数，因此使用 psnr 标准来判定图片的质量，实际上就是计算结果图与原始图像之间的 MSE 而 MSE 是一个统计量，它丢失了图片的结构信息，而人在看图片的时候是能够通过图片中像素点之间的差异抽取图片中的结构信息。因此使用 MSE 作为衡量图片质量的标准可能会出现和人对图片的感知不一致的结果。例如通过人眼观察一张明显失真的图片和一张几乎没有失真的图片，它们和原图计算得出的 MSE 几乎相同，如下图

![原图](http://upload-images.jianshu.io/upload_images/3022282-fa925467773f4ac9.gif)

![meanshift mse=144](http://upload-images.jianshu.io/upload_images/3022282-ca4fd2b0cd0393f6.gif)

![jpg mse=141](http://upload-images.jianshu.io/upload_images/3022282-ecb6e022d439e90b.gif)

## 2 SSIM 算法
文章对图像结构信息的定义：
- 图像结构信息的定义: 独立于平均亮度和分辨率的, 能够表示场景中对象的结构的属性(使用局部亮度)

- 算法:
![ssim](http://upload-images.jianshu.io/upload_images/3022282-972feefd979d906b.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)



- 11x11 circular-symmetric Gaussian :
标准偏差(standard deviation )  1.5倍采样率
