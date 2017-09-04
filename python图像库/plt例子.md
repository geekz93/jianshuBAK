## 1 plt-画单幅图像 
- windows下显示中文字体
- plt下的设置

![image.png](http://upload-images.jianshu.io/upload_images/3022282-2e2f3538ffd72fd4.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

```
import matplotlib as mpl
mpl.rc('font', family='SimHei') # windows 下添加字体用于显示中文
fig2 = plt.figure(2)
plt.xlim(0,16)  # 设置 x 轴的值得范围
x = list(range(1,16))
sinl, = plt.plot(x,sindb_err, '-o', label='Sin')  # 设置线型，标签，注意逗号
gaborl, = plt.plot(x,gabor_err, '-^', label='Gabor')
plt.xlabel('迭代次数'); plt.ylabel('重构误差')  # 添加坐标轴标签
plt.legend(handles=[sinl, gaborl])   # 显示legend
plt.show()
```


## 2 plt-subplot 画4个子图
![gabor_plot.png](http://upload-images.jianshu.io/upload_images/3022282-6521680a26f0bb8c.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
```
def plot_dict(dic, parts=4):
    n = dic.shape[1]
    nl = [int(i) for i in np.linspace(0, n-1, parts) ]
    pics = '2'+str(int(parts/2)) # 22表示总数
    plt.figure(1)
    for idx, i in enumerate(nl):
        idx+=1
        ppos =pics+str(idx) # 221表示第一幅图，之后每行按从左往右的顺序画
        plt.subplot(ppos)
        plt.plot(dic[:,i])
    plt.show()
```
- 关闭坐标轴
- 添加文字

```
plt.imshow(im)
plt.axis('off') # 关闭坐标轴，这句要放在绘图函数后
plt.text(106,280,'K=%d'%(idx+1))
```


## 3 subplots画图
- 面向对象画图 `ax0，ax1 ... ` 为子图对象
- 子图共享 x 轴
- fig1 对象调整子图间距
- 子图添加标题，公式输入
- 子图设置legend

![](http://upload-images.jianshu.io/upload_images/3022282-ce948c0a0f2441ce.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

```
##plot 重构与分解图
fig1, ((ax0, ax1), (ax2, ax3))=  plt.subplots(nrows=2, ncols=2, sharex=True, figsize=(8,8)) # 设置画布，行列数，共享坐标轴
fig1.subplots_adjust(wspace=0.1, hspace=0.2)
ax0.set(title=r'$y1+y2+y3$', xlabel='(a)')
ax0.plot(y, label='signal')
ax0.plot(sindb_recon[2], '-.', label='recon-Sin')
ax0.plot(gabor_recon[2], '--', label='recon-Gabor')
ax0.legend()
ax1.set(title=r'$y1=3sin(4\pi t+\pi/3)$', xlabel='(b)')
ax1.plot(y1, label='signal')
ax1.plot(sindb_atoms[0], '-.', label='recon-Sin')
ax1.plot(gabor_atoms[0], '--', label='recon-Gabor')
# ax1.legend()
ax2.set(title=r'$y2=sin(10\pi t+\pi/6)$', xlabel='(c)')
ax2.plot(y2,label='signal')
ax2.plot(sindb_atoms[1], '-.',label='recon-Sin')
ax2.plot(gabor_atoms[1], '--',label='recon-Gabor')
# ax2.legend()
ax3.set(title=r'$y3=sin(46\pi t)$', xlabel='(d)')
ax3.plot(y3,label='signal')
ax3.plot(sindb_atoms[2], '-.',label='recon-Sin')
ax3.plot(gabor_atoms[2], '--',label='recon-Gabor')
```

## 4 显示图片
- 显示浮点灰度图像
- 隐藏坐标轴
- 在任意位置显示文字


![](http://upload-images.jianshu.io/upload_images/3022282-bc6bda466d390c33.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


```
def showimg(fname='test.png'):
    '''matplotlib库的保存图片，多个子图
    子图调整：去坐标，设置画布大小，标题
    '''
    f, (ax0, ax1, ax2) = plt.subplots(1,3) # figsize=(5,2.8)只能单方向（单参数）调整
    f.subplots_adjust(wspace=0.1) #可以为负值 
    plt.gray()
    ax0.imshow(img_dct.init_img)
    ax0.axis('off')
    ax0.text(106, 280, '(a)', fontsize=18)
    # ax1.set_title('dct')
    ax1.imshow(img_dct.recon_img[2])
    ax1.axis('off')
    ax1.text(112, 280, '(b)', fontsize=18)
    # ax2.set_title('gabor')
    ax2.imshow(img_gabor.recon_img[2])
    ax2.axis('off')
    ax2.text(112, 280, '(c)', fontsize=18)
    # f.savefig(fname)
    plt.show()
```
