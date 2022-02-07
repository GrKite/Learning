This is about the parameters of the function and the default values ^_^
the default value will be in effect only when it is the last parameter (or the function has  all the default values and you can ommit them all, and then all the default values can be seen)
e.g.  

```sql
create or replace procedure p_t
(
       uname IN VARCHAR2 DEFAULT 'paul',
       uid IN NUMBER := 20
)

AS

BEGIN
  dbms_output.put_line(uname || '''s age is ' || uid);
END;
```

res:

- no parameters at all

```sql
SQL> exec p_t();
paul's age is 20
```

- one parameter ''  or null 

   **the first parameter is in effect the same as the parameter transferred into, and the last parameter can be the default value**

``` sql
SQL> exec p_t('');
's age is 20

SQL> exec p_t(null);
's age is 20
```

- two parameters, '' and null still in effect, that means you cannot use the default 'paul' if you transfer other values

```sql
SQL> exec p_t(null,22);
's age is 22

SQL> exec p_t('',22);
's age is 22
```

