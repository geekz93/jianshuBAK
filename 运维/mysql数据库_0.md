转载自: [http://www.cnblogs.com/mr-wid/archive/2013/05/09/3068229.html](http://www.cnblogs.com/mr-wid/archive/2013/05/09/3068229.html)
层级查询: http://database.51cto.com/art/201010/231539.htm

- 创建 root 用户：启动数据库后，root用户就默认创建了，在 mysql数据库中的user表中可以查看，此时root密码为空。可以使用
```
update mysql.user set password=password('w') where host='localhost' and user='root';
```
将mysql库 的root密码设置为 w ，设置完成后需要：
```
flush privileges;
```
修改才能生效

- 登录: `mysql -u root -p[passwd]` -p后面直接跟密码
mysql 语句以 `;` 结尾

- 显示数据库: `show databases;`

- 登录用户后显示数据库中的表：登录用户有 3 个表数据字典 `ALL_TABLES USER_TABLES DBA_TABLES`，分别对应用户有权限看的所有表，用户的表，和具有DBA 权限的表。使用 `select * from USER_TABLE` 查看用户的表

- 选择数据库: `use test_db;` 在操作数据库前需要选择一个数据库

- 显示数据库中的表: `show tables;`

- 创建数据库(create): `create database 数据库名 [其他选项];`, 例如: `create database stud character set gbk;`
```
create database zabbix character set utf8 collate utf8_bin;
```

- 创建表单: `create table 表名称(列声明 数据类型);`

- 插入值(insert): `insert into 表名 [(列名1, 列名2, 列名3, ...)] values (值1, 值2, 值3, ...);` 例如: `insert into stud(name, sex, age) values("zooo", 'm', 18)`

- 查表: `select 列名称 from 表名称 [查询条件];` 例如:
`select * from stud where sex="女";` 显示性别为女的行

- 修改(update): `表名称 set 列名称=新值 where 更新条件;`, 
**例:** `update stud set tel=18300010923 where id=5`

- alter: 
  + 添加字段
```
alter table test add (n0 int, n1 int)
```
  + 修改表名
```
alter table test rename to test2;
```


- 删除表内容(delete): `delete from 表名称 where 删除条件;`,
**例:** `delete from stud where age=24`
truncate table abc

- 删除表空间: drop tablespace tablename
- 删除表结构: drop table tablename

## 创建表单
```
create table students
	（
		id int unsigned not null auto_increment primary key,
		name char(8) not null,
		sex char(4) not null,
		age tinyint unsigned not null,
		tel char(13) null default "-"
	);
```
以 "id int unsigned not null auto_increment primary key" 行进行介绍:
- "id": 为列的名称;
- "int": 指定该列的类型为 int(取值范围为 -8388608到8388607), 在后面我们又用 "unsigned" 加以修饰, 表示该类型为无符号型, 此时该列的取值范围为 0到16777215;
- "not null": 说明该列的值不能为空, 必须要填, 如果不指定该属性, 默认可为空;
- "auto_increment": 需在整数列中使用, 其作用是在插入数据时若该列为 NULL, MySQL将自动产生一个比现存值更大的唯一标识符值。在每张表中仅能有一个这样的值且所在列必须为索引列。
- "primary key": 表示该列是表的主键, 本列的值必须唯一, MySQL将自动索引该列。
