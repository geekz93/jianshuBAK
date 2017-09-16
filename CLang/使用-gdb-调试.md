## 基本操作
编译的时候加上 `-g` 参数
`g++ -g -o chain single_chain.cpp`
- 进入调试：
```
gdb chain//进入gdb
b main //设置断点为 main 函数
r //执行，在开始调试的时候需要先使用 r 执行
```
- 执行到下一个断点：`c`
- 单步执行：`n`
- 进入函数：`s`
- 退出函数：`finish`
- 显示变量：`p variety`
按回车默认执行上一条命令

## 进一步
- 跟踪变量: `disp var` 可以设置多个,每次单步时都会显示变量的值
- 取消跟踪: `undisp num` num为已经跟踪的变量的序号
- 设置变量的值:`set var=2`
