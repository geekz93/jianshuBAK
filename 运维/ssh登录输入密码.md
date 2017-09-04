执行像ssh,scp这类secure command时,必须手工输入密码,而且它们是直接从/dev/tty而不是stdin中读取密码的,这也意味着无法通过重定向IO的方式传送密码給这些程序.
http://www.th7.cn/Program/Python/201611/1012964.shtml
