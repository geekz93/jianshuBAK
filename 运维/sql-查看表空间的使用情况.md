- sql:
```
select 表空间名, sum(字节数), sum(已使用), sum(剩余空间),sum(已使用)*100/sum(字节数)
  from (select b.file_id as 文件ID号,
               b.tablespace_name as 表空间名,
               b.bytes / 1024 / 1024 as 字节数,
               (b.bytes - sum(nvl(a.bytes, 0))) / 1024 / 1024 as 已使用,
               sum(nvl(a.bytes, 0)) / 1024 / 1024 as 剩余空间
          from dba_free_space a, dba_data_files b
         where a.file_id(+) = b.file_id
         group by b.tablespace_name, b.file_id, b.bytes)
 group by 表空间名
 order by 表空间名;
```

- 基本句式: `select ... from ...` 使用 `as` 起别名: `select 表空间名, sum(字节数) as 字节数`, 显示表头为 字节数
- group by: 将数据按照 **表空间名** 分类汇总, 使用 `sum` 函数是将同类的数据相加
- order by: 按照类别排序, 默认为升序, 使用 `desc` 改为降序排列
- nvl函数: oracle提供的函数, NVL(E1, E2)的功能为：如果E1为NULL，则函数返回E2，否则返回E1本身。

但此函数有一定局限，所以就有了NVL2函数。拓展：NVL2函数:Oracle/PLSQL中的一个函数,Oracle在NVL函数的功能上扩展，提供了NVL2函数。NVL2(E1, E2, E3)的功能为：如果E1为NULL，则函数返回E3，若E1不为null，则返回E2。
