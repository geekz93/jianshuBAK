- 不使用rm -rf
- 使用将rm重定向到mv

```
#~/.bashrc
rm2mv(){
    tdir=~/.rm2dir/$(date +%Y%m%d%H%M%S)
    mkdir -p $tdir
    mv "$@" $tdir
}

alias rm=rm2mv
```
在rm文件名为`~`时报错，no permission
