- 参考: http://www.poluoluo.com/jzxy/201011/98780.html
当用户要跨本地数据库，访问另外一个数据库表中的数据时，本地数据库中必须创建了远程数据库的dblink,通过dblink本地数据库可以像访问本地数据库一样访问远程数据库表中的数据

- 当前用户必须具有创建 dblink 的权限


- 创建 dblink:
```
create public database link pms_dblink
connect to PMS identified by pms01
using '(DESCRIPTION =
(ADDRESS_LIST =
(ADDRESS = (PROTOCOL = TCP)(HOST =xx.xx.xx.xx)(PORT = 1521))
)
(CONNECT_DATA =
(SERVICE_NAME =serviceName)
)
)';
```
dblink对象名: pms_dblink
远程数据库用户: PMS
该用户的密码: pms01

- 查看已经建立的 dblink: select * from dba_db_links;
