## scipy.signal.convolve2d 二维卷积
```
### convolve test ####
arr1 = np.ones((4,4))
arr2 = np.ones((3,3))
print(convolve2d(arr1, arr2, 'valid'))
```

## scipy.optmize.root求解一元多次方程
用法 optmize.root(f,x0)
解 x^3+x-1=0
` optimize.root(lambda x: x**3+x-1, 234234)`
x0:初值（不理解它是什么意思），从实验来看，x0越大，结果的精度越高，如果x0为[34, 342]，则结果的x值也有两个。对于有两个x解的情况，传如x0=[xxx,xxx]有时可以求出l这两个解

## scipy.cluster.vq模块
```python
vq.vq(obs, code_book, check_finite=True)
```
- 输入： 
  * obs： MxN 矩阵，每列为一个观测向量
  * code_book: 字典，每行为字典中的一个原子
- 输出： 
  * code： M个原子索引
  * dist： 被选出的原子和观测向量的距离（两向量的距离，即差向量的模长）
