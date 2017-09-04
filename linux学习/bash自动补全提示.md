各位童鞋们过节好啊，今天给大家带来的是在bash中DIY制表符键自动补全。bash是大多数主流Linux发行版的默认shell，如果你用过bash，那么一定会接触到<tab>键自动补全的这个方便的功能，当你一个命令的头几个字符敲下去，按下<tab>，如果以此开头的命令只有1个， bash会直接帮你补全，如果有多个，则会有相应提示，而在后续的参数输入时，也会带有默认的自动补全文件路径的功能。当你习惯了<tab>，很难想象没有自动补全的日子会是什么样子。bash默认支持常见的补全功能，如可执行命令、文件路径等，如果安装了bash-completion包，甚至连chown, man, svn, ssh这些也会带有相应的自动补全提示，而不是单纯的文件路径补全。好奇的你一定想知道是怎么实现的吧，其实很简单，我们举个例子来说：假定你有一个命令，叫做abc，它又有自己的子命令，分别是build_all、compile和update，其中compile这个子命令需要的参数必须来自project.list这个文件中列出的值，怎么实现<tab>自动补全，让bash知道abc的合法子命令和compile子命令的合法参数列表呢？在你的~/.bashrc或者任何一个启动bash时会被执行的文件中加入下面的代码：
```
function _abc() {    
COMPREPLY=()    
local cur=${COMP_WORDS[COMP_CWORD]};   
 local com=${COMP_WORDS[COMP_CWORD-1]};    
case $com in    'abc')        
COMPREPLY=($(compgen -W 'build_all compile update' -- $cur))        
;;   
 'compile')        
local pro=($(awk '{print $1}' project.list))        
COMPREPLY=($(compgen -W '${pro[@]}' -- $cur))        
;;    
*)        
;;    
esac    
return 0}
complete -F _abc abc
```
手动载入一下，或者重启bash，再敲abc命令，即可自动补全子命令，如果子命令是compile，还能自动补全相应的参数值。我们来简单分析一下这段代码。首先我们定义一个function _abc，这个函数先清空自动补全列表，根据当前输入位置前一个token判断目前需要自动补全的语境，如果是abc，则将自动补全内容设置为'build_all'、'compile'和'update'，如果是'compile'，则将project.list文件内容输出到补全列表，当然，这里我们也可以换成其他任何必要的方式。最后我们通过complete -F _abc abc将这段自动补全逻辑注册到abc这个主词上。这样当我们敲abc时，后续内容就能自动补全了。Enjoy!
