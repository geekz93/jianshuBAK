- 在 git clone 的时候出现 Permission denied (publickey)
  * 原因：不明
  * 解决方法：使用 https 的方式 clone

- 在 push 的时候每次都要输入密码
  * 原因：remote origin 使用的 https 的方式
  * debug：
```
 git remote rm origin
 git remote add origin git@github.com:supertab/gcode.git
```
