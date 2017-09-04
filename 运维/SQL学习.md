- union: 将多张表的查询结果和在一起, 默认去重, 显示全部使用 union all

- 查看建表 sql 出错:
select dbms_metadata.get_ddl('table',' nm_ucapes_var_def') from dual;

## 查询 select ... from ...
- select xx1, xx2 from table2 where yy=dd
select 后面的参数为列约束, where 后面的表达式为行约束

- 去重: select distinct xx from xxx

- 设置选取条件: 
  where, 不等于符号: `<>`, 文本周围使用单引号,或双引号, 数值不需要加

- 逻辑运算符: and 和 or

- 使用圆括号 `()` 组成复杂表达式

- order by 对结果进行排序: `SELECT Company, OrderNumber FROM Orders ORDER BY Company desc`, 逆序显示: `desc`, 顺序显示: `asc`(默认为顺序显示)
多级排序: `order by id, company` 先按照 id 排, 再在之前的基础上按照 company 排

- `group by` 分类汇总, 统计相同项出现的次数 count(attr), 求和 sum(attr) 等....
