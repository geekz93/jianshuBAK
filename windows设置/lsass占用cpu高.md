- **原因，修改了用户密码，然后打开浏览器导致的**
- **解决方法：**
cmd下：
```
RD /s /q "%USERPROFILE%\AppData\Roaming\Microsoft\Protect"
```
