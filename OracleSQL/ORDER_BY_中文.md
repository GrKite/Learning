```sql
WITH A AS (SELECT '{' NAME FROM dual UNION ALL
           SELECT '%' NAME FROM dual UNION ALL
           SELECT '中' NAME FROM dual UNION ALL
           SELECT '鑫' NAME FROM dual UNION ALL
           SELECT '木' NAME FROM dual UNION ALL
           SELECT '酥' NAME FROM dual UNION ALL
           SELECT '贴' NAME FROM dual UNION ALL
           SELECT '多' NAME FROM dual UNION ALL
           SELECT '空' NAME FROM dual UNION ALL
           SELECT '-' NAME FROM dual)
       SELECT NAME, ascii(NAME)
       FROM A
       ORDER BY NAME;
```

res: 

```sql
1	%	37
2	-	45
3	{	123
4	多	46816
5	空	49109
6	木	50366
7	酥	52182
8	贴	52473
9	中	54992
10	鑫	63182
```

