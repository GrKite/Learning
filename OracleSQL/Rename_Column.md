## Oracle Rename Column table syntax:

1. To rename a column in oracle we have to use **rename column** statement
2. You have to use **rename column** statement along with **alter table** statement
3. The RENAME COLUMN statement allows us to rename an existing column in an existing table in any schema (except the schema SYS).

```
ALTER TABLE
   table_name
RENAME COLUMN
old_column_name 
TO
new_column_name;
```

