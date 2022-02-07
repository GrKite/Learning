PARTITION BY IS A analytical function, 

it doesn't affect the total rows of the table or the query results, it only describes the property of the distinct row and rank it. You can use them and then know what happened there...



rank() over (partition by ... order by ...)

e.g.  scott.emp

test 1.

``` sql
select t.* , rank() over (partition by t.deptno order by t.ename) from emp t;
```

test 2.

```sql
select t.* , rank() over (partition by t.job order by t.sal), rank() over (partition by t.deptno order by t.ename) from emp t;
```

test 3.

```sql
select t.* , rank() over (partition by t.job order by t.sal) from emp t;
```

test 4.

```sql
 select * from emp;
```



1. task is CMIS   19:00 - 20:00

   

2. 303B0             20:00 - 21:00

3. today I think we need to do things that is really awesome...

