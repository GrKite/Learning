1. 当入参是NUMBER类型, 传入 ' ' (空格), 会进行报错, 可以更改数据类型为varchar2, 这样就不会发生错误的说.

e.g.

```sql
create or replace procedure sp_num_char
(i_num IN number,
 i_ch  IN varchar2)
AS
BEGIN
  IF i_ch IS NULL THEN
    dbms_output.put_line(i_ch || 'is null');
  END IF;
END;
```

- note: the in-params in the sp, the data type is the general data type like number, varchar2, but not exact data type such as number(2), varchar2(2).

  

```sql
DECLARE
BEGIN
  sp_num_char(' ', ''); -- the first one is ' ' a space, and the second one is '' 空字符
END;
```

the result:

```sql
ORA-06502: PL/SQL: 数字或值错误 :  字符到数值的转换错误
ORA-06512: 在 line 3
```



字符串类型的话, 就会保留相应的空白字符啦, 然后就可以继续执行下去啦, 按说我觉得嘛, 最好还是用数字类型的接口比较好的说.

主要原因是ini使用了字符串类型, 但是sp接口里面的是数字类型, 所以会将' '空白字符串传递过来, 由此发生错误, 保险起见, 最好是换一下ini里面的数据类型, 保持和sp里面一致, 这样比较方便, 就不会产生问题的说了. 

或者换一下sp里面的参数类型, 保持也是字符串类型, 这样也是可以的说. 





