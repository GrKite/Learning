#### rownum

自动的行号编号

- 发现rownum不属于emp表的数据列, 但是由于是伪列, 所以可以使用. 发现了rownum是针对于每一行的数据, 自动进行了编号. 但是这个自动编号是动态生成的.

- 

  ```sql
  SQL> select * from emp where rownum = 1;
  ```

  这个只有rownum = 1才有用, 其余的就都没有用的说

  **取出第一行记录** # 便于观察的说

  **取出多行记录**  # 便于查询

  ```sql
  SQL> select rownum, empno from emp where rownum <= 5;
  
      ROWNUM      EMPNO
  ---------- ----------
           1       7369
           2       7499
           3       7521
           4       7566
           5       7654
  ```

   rn , 这里必须要 起别名才能用的说哇

  ```sql
  SQL> select y.* from (select rownum rn,emp.* from emp) y where y.rn <= 3;
  
          RN      EMPNO ENAME      JOB              MGR HIREDATE              SAL       COMM     DEPTNO
  ---------- ---------- ---------- --------- ---------- -------------- ---------- ---------- ----------
           1       7369 SMITH      CLERK           7902 17-12月-80            800                    20
           2       7499 ALLEN      SALESMAN        7698 20-2月 -81           1600        300         30
           3       7521 WARD       SALESMAN        7698 22-2月 -81           1250        500         30
  ```

  