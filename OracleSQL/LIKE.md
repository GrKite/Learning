**Escape character**(转义字符)： escape '<character>'

e.g.

```sql
SQL> select last_name, hire_date, salary, department_id from employees where last_name like '%\_%' escape '\';
LAST_NAME                 HIRE_DATE       SALARY DEPARTMENT_ID
------------------------- ----------- ---------- -------------
Wha_len                   1987/9/17      4400.00            10
```



```sql
SQL> select last_name, hire_date, salary, department_id from employees where last_name like '%#_%' escape '#';
LAST_NAME                 HIRE_DATE       SALARY DEPARTMENT_ID
------------------------- ----------- ---------- -------------
Wha_len                   1987/9/17      4400.00            10
```

