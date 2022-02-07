![image-20210924193205859](C:\Users\duoduo.liu\AppData\Roaming\Typora\typora-user-images\image-20210924193205859.png)

- insert into 语句 的话， 可以用select语句来获得需要的语句， 其中两个表中的字段名可以不一样， 但是值的数量需要相等，否则会报错

  ```sql
  SQL> insert into duoduo2 select * from duoduo3;
  insert into duoduo2 select * from duoduo3
              *
  第 1 行出现错误:
  ORA-00947: 没有足够的值
  ```

  

```sql
SQL> insert into duoduo2 select * from duoduo1;
insert into duoduo2 select * from duoduo1
            *
第 1 行出现错误:
ORA-00913: 值过多
```

