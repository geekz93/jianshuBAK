- `max(hire_date)`: hire_date列中的最大值
- `limit 2, 1`: 从第3行开始，取1行
```
select * from employees order by hire_date desc limit 2,1;
```
- `PRIMARY KEY (emp_no,from_date)`: 插入的元素中`emp_no`和`from_date`这两个属性不能都相等，其中一个是可以相等的
