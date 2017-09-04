## event 事务
- 开启一个 sql 窗就是建立了一次 session, 在session 改动了数据库中的数据(insert, delete, update) 需要进行 commit 操作这些数据才会实际发生变动, 否者数据的改动只在这次 session 有用. 如果不想使数据库中的数据发生变化在关闭 session 前使用 rallback 撤销之前的修改

## 内连接&自然连接
- 使用像` = ` 或 `<>` 之类的比较运算符
- 获取两表的公共部分

## 外连接
- outer join (+): http://blog.chinaunix.net/uid-21187846-id-3288525.html
- (+) 例子: http://bbs.csdn.net/topics/230049164


![outer_join](http://upload-images.jianshu.io/upload_images/3022282-32db25fb47b30215.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

## 函数
- round:
  * 四舍五入, 可以设置保留精度
  * 可以处理日期, 四舍五入
- to_date: 格式化日期
  * [http://www.cnblogs.com/lslvxy/p/3457049.html](http://www.cnblogs.com/lslvxy/p/3457049.html)

- 正则 regexp_substr ():
  * 删除file_name 字段中含有 01_HR 的项
`delete from nm_capes2_log_val where regexp_substr(file_name, '_01HR')='_01HR'`

## sysdate
- 加法: 
```
 select sysdate,add_months(sysdate,12) from dual;        --加1年
 select sysdate,add_months(sysdate,1) from dual;        --加1月
 select sysdate,to_char(sysdate+7,'yyyy-mm-dd HH24:MI:SS') from dual;   --加1星期
 select sysdate,to_char(sysdate+1,'yyyy-mm-dd HH24:MI:SS') from dual;   --加1天
 select sysdate,to_char(sysdate+1/24,'yyyy-mm-dd HH24:MI:SS') from dual;  --加1小时
 select sysdate,to_char(sysdate+1/24/60,'yyyy-mm-dd HH24:MI:SS') from dual;  --加1分钟
 select sysdate,to_char(sysdate+1/24/60/60,'yyyy-mm-dd HH24:MI:SS') from dual;  --加1秒
```
- 减法:
```
 select sysdate,add_months(sysdate,-12) from dual;        --减1年
 select sysdate,add_months(sysdate,-1) from dual;        --减1月
 select sysdate,to_char(sysdate-7,'yyyy-mm-dd HH24:MI:SS') from dual;   --减1星期
 select sysdate,to_char(sysdate-1,'yyyy-mm-dd HH24:MI:SS') from dual;   --减1天
 select sysdate,to_char(sysdate-1/24,'yyyy-mm-dd HH24:MI:SS') from dual;  --减1小时
 select sysdate,to_char(sysdate-1/24/60,'yyyy-mm-dd HH24:MI:SS') from dual;  --减1分钟
 select sysdate,to_char(sysdate-1/24/60/60,'yyyy-mm-dd HH24:MI:SS') from dual;  --减1秒
```

- **表重命名：**  rename test1 to test
