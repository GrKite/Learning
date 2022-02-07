https://www.cnblogs.com/guixiaoming/p/6516261.html  LEFT JOIN (Detailed instructions)

SQL> select * from product_details;
              ID              WEIGHT                EXIST

----------- ----------- -----------
          2          22           0
          4          44           1
          5          55           0
          6          66           1





SQL> select * from product;
         ID      AMOUNT

----------- -----------
          1         100
          2         200
          3         300
          4         400





```
SELECT * FROM product a LEFT JOIN product_details b
       ON a.id=b.id AND b.weight!=44 AND b.exist=0
       WHERE b.id IS NULL;
```

