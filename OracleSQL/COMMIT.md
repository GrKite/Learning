# COMMIT

![image-20211228164224798](C:\Users\duoduo.liu\AppData\Roaming\Typora\typora-user-images\image-20211228164224798.png)

Oracle Database issues an implicit `COMMIT` before and after any data definition language (DDL) statement.



> references: 
>
> https://docs.oracle.com/cd/B19306_01/server.102/b14200/statements_4010.htm (nearly official documentation)
>
> https://blog.csdn.net/hzhsan/article/details/9719307 (chinese summary)



- COMMIT 可以保证数据一致性, PL/SQL的话, 在test sp之后, 数据是和test里面输入的数据一致.
