## 判断语句
- if...; then ... fi语法
```
if condition; then
    command
    command
elif condition; then
    command
fi
```
- 例子: 
```
#!/usr/bin/bash
if [[ "$1" == "download" ]]; then
        echo 1
elif [[ "$1" == "upload" ]]; then
        echo 2
else
        echo "Usage: ./git.sh upload|download"
fi
```

- 注意:
    * if 和 test 配和使用, [ expression ] 是 test 的相同形式
    * expression 要注意空格: $str1==$str2 是错误用法, 正确为 $str1 == $str2, 才能起到比较的作用
    * 对于`[ express ]`形式的比较大小,使用 >, < 号时, 要用转义符转义. `[[ express ]]` 则不需要. 比较字符串大小是按照 locate 定义字符集中的字符顺序进行比较
    * 比较数字使用 `-eq` 比较字符串使用 `==`
    * 使用双引号包括变量`"$1"`避免因为空输入而出现的报错

- 如果 if 后面跟着命令序列, 则最后一个命令的执行结果作为 if 的判断条件
```
[me@linuxbox ~]$ if false; true; then echo "It's true."; fi
It's true.
[me@linuxbox ~]$ if true; false; then echo "It's true."; fi
[me@linuxbox ~]$ 
```

- exit n: 退出脚本, 后面加的数字保存在变量 $? 中
```
退出码（exit status，或exit code）的约定：
0表示成功（Zero - Success）
非0表示失败（Non-Zero  - Failure）
2表示用法不当（Incorrect Usage）
127表示命令没有找到（Command Not Found）
126表示不是可执行的（Not an executable）
```

- case语法
```
case 字符串 in
    模式)
        语句
        ;;
    模式2 | 模式3)
         语句
         ;;
    *)
         默认执行的 语句
         ;;
esac
提示：esac就是case反过来写。
```
- 例子
```
    case $1 in  
        男 | M)  
            echo "是位小少爷"  
            ;;  
        女 | F)  
            echo "是位小千金"  
            ;;  
        *)  
            echo "有没有搞错"  
            ;;  
    esac  
```

## shell 中括号的作用
http://blog.csdn.net/taiyang1987912/article/details/39551385
  - [[ 的作用：
[[是 bash 程序语言的关键字。并不是一个命令，使用[[ ... ]]条件判断结构，而不是[ ... ]，能够防止脚本中的许多逻辑错误。比如，&&、||、<和> 操作符能够正常存在于[[ ]]条件判断结构中，但是如果出现在[ ]结构中的话，会报错

- echo不忽略换行： 
直接使用 echo 输出字符串：
```
echo "one two three
1 2 3
1 2 3
1 2 3"
```
输出变量中的换行, 对变量用双引号包住可输出换行, 否则忽略换行
```
d="one two three
1 2 3
1 2 3
1 2 3"
echo "$d"
```

- 读取输入: read
```
read -t 10 -p "enter sth: " var
```
交互输入,将输入的内容保存到变量 var 中
