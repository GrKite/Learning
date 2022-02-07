所谓视图

```sql
create view myview as
select d.deptno, d.dname, d.loc,temp.count, temp.avg
from dept d, (
	select deptno dno, count(empno) count, avg(sal) avg from emp
    group by deptno) temp
    where d.deptno = temp.dno(+);
```



```sql
create or replace view myview as
select * from emp where deptno = 20;
```



```sql
create or replace view myview as
select * from emp where deptno = 20
with check option;
```



```sql\
create or replace view myview as
select * from emp where deptno = 20
with read only;
```



```sql
drop view 视图名
```

1. 如果是标准的开发, 强烈建议使用视图, 
2. 视图一般建议创建只读视图