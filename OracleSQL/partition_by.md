over (partition by ... order by ...)

#### sum(<column_name>) over (partition by ... order by ...) 



- This will calculate the sum of the same <column_name>, and partition it by deptno

  ​    --> sum(sal) over(partition by deptno) 

```sql
SQL> select deptno,ename,sal,sum(sal) over(partition by deptno) from emp ;
DEPTNO ENAME            SAL SUM(SAL)OVER(PARTITIONBYDEPTNO
------ ---------- --------- ------------------------------
    10 CLARK        2450.00                           8750
    10 KING         5000.00                           8750
    10 MILLER       1300.00                           8750
    20 JONES        2975.00                          10875
    20 FORD         3000.00                          10875
    20 ADAMS        1100.00                          10875
    20 SMITH         800.00                          10875
    20 SCOTT        3000.00                          10875
    30 WARD         1250.00                           9400
    30 TURNER       1500.00                           9400
    30 ALLEN        1600.00                           9400
    30 JAMES         950.00                           9400
    30 BLAKE        2850.00                           9400
    30 MARTIN       1250.00                           9400
14 rows selected
```

- If you want to see the differences from the different sequences, using order by , be careful with the same order sequence...


```sql
  SQL> select ename,sal,sum(sal) over(order by sal,empno) as total1,sum(sal) over(order by sal)as total2 , rank() over (order by sal) rank from emp;
  ENAME            SAL     TOTAL1     TOTAL2       RANK
  ---------- --------- ---------- ---------- ----------
  SMITH         800.00        800        800          1
  JAMES         950.00       1750       1750          2
  ADAMS        1100.00       2850       2850          3
  WARD         1250.00       4100       5350          4 -- the same rank, calculate together
  MARTIN       1250.00       5350       5350          4 -- the same rank, calculate together
  MILLER       1300.00       6650       6650          6
  TURNER       1500.00       8150       8150          7
  ALLEN        1600.00       9750       9750          8
  CLARK        2450.00      12200      12200          9
  BLAKE        2850.00      15050      15050         10
  JONES        2975.00      18025      18025         11
  SCOTT        3000.00      21025      24025         12 -- the same rank, calculate together
  FORD         3000.00      24025      24025         12	-- the same rank, calculate together
  KING         5000.00      29025      29025         14
```

  

note: if it is not the same rank, it has no problem. ^_^ 

