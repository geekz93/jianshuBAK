1. 先破解
2. 更改注册表
点击“开始”——点击“运行”——输入“regedit”回车确定（或者WIN +  R  快捷组合键也可以打开运行，然后输入 regedit 进入注册表编辑器)找到
HKEY_CURRENT_USER\Software\Microsoft\Office\14.0\Word\Options 看见右边有一个 NoRereg 的属性，如果没有这个属性，请自己用鼠标右键新建一个，值为DWORD(32位)，命名NoRereg，十六进制，数值数据为1 ，完成后退出。
