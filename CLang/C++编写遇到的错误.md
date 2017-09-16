## 编译不通过类型
0. 类定义,忘记在最后的花括号后加分号
  - debug: 加上即可
1. 类中报错:`error: invalid use of non-static data member Chain::length`
  -  类中的函数,直接使用类中的变量作为函数的默认值
```
class Chain{
public:
    Chain():length(0){}
    int find(int pos=length);
    int length;
}
```

  - dubeg: 折中法, 先给 pos 赋值, 再在函数实现中判断后赋值
```
int find(int pos=-1);
int find(int pos){
    if(pos==-1) pos=length;
}
```

### 逻辑错误类型
0. if 中漏写等号:`if(pos=2)`
  - debug: 检查每一个 if 语句, 修改成 `if(pos==2)`
