If you want to find the definite data in where condition, NULL is unknown and it will not show in the not equal situation ;)

e.g.

```sql
SQL> select * from emp;
EMPNO ENAME      JOB         MGR HIREDATE          SAL      COMM DEPTNO
----- ---------- --------- ----- ----------- --------- --------- ------
 7369 SMITH      CLERK      7902 1980/12/17     800.00               20
 7499 ALLEN      SALESMAN   7698 1981/2/20     1600.00    300.00     30
 7521 WARD       SALESMAN   7698 1981/2/22     1250.00    500.00     30
 7566 JONES      MANAGER    7839 1981/4/2      2975.00               20
 7654 MARTIN     SALESMAN   7698 1981/9/28     1250.00   1400.00     30
 7698 BLAKE      MANAGER    7839 1981/5/1      2850.00               30
 7782 CLARK      MANAGER    7839 1981/6/9      2450.00               10
 7788 SCOTT      ANALYST    7566 1987/4/19     3000.00               20
 7839 KING       PRESIDENT       1981/11/17    5000.00               10
 7844 TURNER     SALESMAN   7698 1981/9/8      1500.00      0.00     30
 7876 ADAMS      CLERK      7788 1987/5/23     1100.00               20
 7900 JAMES      CLERK      7698 1981/12/3      950.00               30
 7902 FORD       ANALYST    7566 1981/12/3     3000.00               20
 7934 MILLER     CLERK      7782 1982/1/23     1300.00               10
14 rows selected

-- <> situation , and NULL is not in the result set
SQL> select * from emp where mgr <> 7698;
EMPNO ENAME      JOB         MGR HIREDATE          SAL      COMM DEPTNO
----- ---------- --------- ----- ----------- --------- --------- ------
 7369 SMITH      CLERK      7902 1980/12/17     800.00               20
 7566 JONES      MANAGER    7839 1981/4/2      2975.00               20
 7698 BLAKE      MANAGER    7839 1981/5/1      2850.00               30
 7782 CLARK      MANAGER    7839 1981/6/9      2450.00               10
 7788 SCOTT      ANALYST    7566 1987/4/19     3000.00               20
 7876 ADAMS      CLERK      7788 1987/5/23     1100.00               20
 7902 FORD       ANALYST    7566 1981/12/3     3000.00               20
 7934 MILLER     CLERK      7782 1982/1/23     1300.00               10
8 rows selected

-- <> situation and is null situation , and NULL is in the result set
SQL> select * from emp where mgr is null;
EMPNO ENAME      JOB         MGR HIREDATE          SAL      COMM DEPTNO
----- ---------- --------- ----- ----------- --------- --------- ------
 7839 KING       PRESIDENT       1981/11/17    5000.00               10
-- is null situation , but NULL is in the result set
SQL> select * from emp where mgr <> 7698 or mgr is null;
EMPNO ENAME      JOB         MGR HIREDATE          SAL      COMM DEPTNO
----- ---------- --------- ----- ----------- --------- --------- ------
 7369 SMITH      CLERK      7902 1980/12/17     800.00               20
 7566 JONES      MANAGER    7839 1981/4/2      2975.00               20
 7698 BLAKE      MANAGER    7839 1981/5/1      2850.00               30
 7782 CLARK      MANAGER    7839 1981/6/9      2450.00               10
 7788 SCOTT      ANALYST    7566 1987/4/19     3000.00               20
 7839 KING       PRESIDENT       1981/11/17    5000.00               10
 7876 ADAMS      CLERK      7788 1987/5/23     1100.00               20
 7902 FORD       ANALYST    7566 1981/12/3     3000.00               20
 7934 MILLER     CLERK      7782 1982/1/23     1300.00               10
9 rows selected
```
