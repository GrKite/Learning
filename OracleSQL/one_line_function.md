lower()

upper()

initcap()

```sql
SQL> select lower('ATGUIGUJAVA'),UPPER('atguigu Java'),initcap('atGuiGu java') from dual;

LOWER('ATGUIGUJAVA') UPPER('ATGUIGUJAVA') INITCAP('ATGUIGUJAVA')
-------------------- -------------------- ----------------------
atguigujava          ATGUIGU JAVA         Atguigu Java
```



concat()

substr()

length()

```sql
SQL> select concat('aaa','bbb'), substr('helloworld',2,4), length('aaa') from dual;
CONCAT('AAA','BBB') SUBSTR('HELLOWORLD',2,4) LENGTH('AAA')
------------------- ------------------------ -------------
aaabbb              ello                                 3
```



sysdate()



日期的数学运算:

1. 加， 减 数字， 可以获得相应的日期

```sql
SQL> select sysdate, sysdate+1, sysdate-2 from dual;
SYSDATE     SYSDATE+1   SYSDATE-2
----------- ----------- -----------
2021/8/7 15 2021/8/8 15 2021/8/5 15
```

2. 

```sql
SQL> select add_months(sysdate,2), add_months(sysdate,-3),next_day(sysdate,'星期日') from dual;
ADD_MONTHS(SYSDATE,2) ADD_MONTHS(SYSDATE,-3) NEXT_DAY(SYSDATE,'星期日')
--------------------- ---------------------- --------------------------
2021/10/7 15:43:46    2021/5/7 15:43:46      2021/8/8 15:43:46
```



```sql
SQL> select last_day(add_months(sysdate, -1)) last_day_last_month, last_day(add_months(sysdate,1)) last_day_next_month from dual;
LAST_DAY_LAST_MONTH LAST_DAY_NEXT_MONTH
------------------- -------------------
2021/7/31 15:54:52  2021/9/30 15:54:52
```



3. round(<date>)   trunc(<date>)  

   ```sql
   SQL> select round(sysdate,'month'),round(sysdate,'mm'), trunc(sysdate,'hh') from dual;
   ROUND(SYSDATE,'MONTH') ROUND(SYSDATE,'MM') TRUNC(SYSDATE,'HH')
   ---------------------- ------------------- -------------------
   2021/8/1               2021/8/1            2021/8/7 16:00:00
   ```

   





#### Conversion function

1. implicitly conversed (automatically conversed)

   date <=> varchar2 <=> number

   ```sql
   SQL> select '12' + 1 from dual;
       '12'+1
   ----------
           13
   
   SQL> select '12'||1 from dual;
   '12'||1
   -------
   121
   
   SQL> select sysdate+'2' from dual;
   SYSDATE+'2'
   -----------
   2021/8/9 16
   ```

   

2. explicitly conversed

   ![image-20210807161700977](C:\Users\duoduo.liu\AppData\Roaming\Typora\typora-user-images\image-20210807161700977.png)

to_date()

to_char()

to_number()



- number conversed into char: 

```sql
SQL> select to_char(1234567.89, 'L999,999,999.99') from dual; -- 'L' means currency is local currency type
TO_CHAR(1234567.89,'L999,999,9
------------------------------
           ￥1,234,567.89

SQL> select to_char(1234567.89, 'l999,999,999.99') from dual; -- 'L' means currency is U.S currency type
TO_CHAR(1234567.89,'L999,999,9
------------------------------
           ￥1,234,567.89

SQL> select to_char(1234567.89, '$999,999,999.99') from dual; -- '$' means currency is U.S currency type
TO_CHAR(1234567.89,'$999,999,9
------------------------------
   $1,234,567.89

SQL> select to_char(1234567.89, '$000,999,999.99') from dual; --0 if there is null, pad with 0, otherwise, 9 pad with whitespace
TO_CHAR(1234567.89,'$000,999,9
------------------------------
 $001,234,567.89
```



- char  conversed into number: 

```sql
SQL> select to_number('$1,234,567.89','$999,999,999.99') from dual;
TO_NUMBER('$1,234,567.89','$99
------------------------------
                    1234567.89

SQL> select to_number('￥1,234,567.89','L999,999,999.99') from dual;
 TO_NUMBER('￥1,234,567.89','L9
------------------------------
                    1234567.89
```

