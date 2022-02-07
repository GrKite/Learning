# Primary Key



```linux
SQL> create table primary_key_test (id number(2) not null, name varchar2(100), kkk varchar2(20) );
Table created

SQL> alter table primary_key_test add constraint pk_constraint_test PRIMARY KEY (id, name);
Table altered

SQL> INSERT INTO primary_key_test (id, name, kkk) values (1, null, 'hhh');
INSERT INTO primary_key_test (id, name, kkk) values (1, null, 'hhh')
ORA-01400: 无法将 NULL 插入 ("SCOTT"."PRIMARY_KEY_TEST"."NAME")
```



## What is a primary key in Oracle?

In Oracle, a **primary key** is a single field or combination of fields that uniquely defines a record. None of the fields that are part of the primary key can contain a null value. A table can have only one primary key.

## Note

- In Oracle, a primary key can not contain more than 32 columns.
- A primary key can be defined in either a CREATE TABLE statement or an ALTER TABLE statement.



references:

https://www.techonthenet.com/oracle/primary_keys.php#:~:text=You%20can%20create%20a%20primary%20key%20in%20Oracle,constraint_name%20PRIMARY%20KEY%20%28column1%2C%20column2%2C%20...%20column_n%29%20%29%3B