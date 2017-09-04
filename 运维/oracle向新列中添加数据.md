```
select to_char(sysdate,'yyyymmdd') data, '01mi_var' job from dual
```

![](http://upload-images.jianshu.io/upload_images/3022282-467225a7ab566523.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

- **对于通配符，需要指定表的别名**
```
select 'fff' ttt, a.* from quota_extract a
```
