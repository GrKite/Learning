# User vs. schema in Oracle

-  

## An Oracle user asks what the difference is between a user and a schema.

​		 		 		 				 				 			 		 				 				 			 		 				 				 			 		 				 				 			 		 				 			 		 			 		 		 	

​	Published: 10 Jul 2008

 What is the difference between a user and a schema?

 Technically, a schema is a collection of database objects owned by a  specific user. Those objects include tables, indexes, views, stored  procedures, etc. In Oracle, a schema requires a user to be created. But  you can create a user that has no schema (i.e, no objects). So in  Oracle, the user is the account and the schema is the objects. It is  possible in other database platforms to have a schema without a user.  



==> So in  Oracle, the user is the account and the schema is the objects.

https://searchoracle.techtarget.com/answer/User-vs-schema-in-Oracle#:~:text=In%20Oracle%2C%20a%20schema%20requires%20a%20user%20to,platforms%20to%20have%20a%20schema%20without%20a%20user.



一个挺形象的比喻：schema如房子，user如房子的主人
user即Oracle中的用户，和所有系统的中用户概念类似，用户所持有的是系统的权限及资源；而schema所涵盖的是各种对象，它包含了表、函数、包等等对象的“所在地”，并不包括对他们的权限控制。好比一个房子，里面放满了家具，对这些家具有支配权的是房子的主人（user），而不是房子（schema）。你可以也是一个房子的主人（user），拥有自己的房子（schema）。

可以通过alter session的方式进入别人的房子。这个时候，你可以看到别人房子里的家具（desc）。如果你没有特别指定的话，你所做的操作都是针对你当前所在房子中的东西。至于你是否有权限使用（select）、搬动（update）或者拿走（delete）这些家具就看这个房子的主人有没有给你这样的权限了，或者你是整个大厦（DB）的老大（DBA）。alter session set schema可以用来代替synonyms。

如果你想调用其他schema的对象（有权限的前提下），但并没有建synonym，同时又不想把其他schema名字放入代码中，就可以首先使用alter session set schema=<其他schema名字>。 



