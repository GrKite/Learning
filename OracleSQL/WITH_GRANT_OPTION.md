表的赋权语句没有WITH GRANT OPTION 有时会导致报错 ORA-01720: grant option does not exist

用户权限不同，实施部署的时候，使用sys权限，即使没有with grant option 仍可成功赋权；

大华银行部署时不使用sys权限， 会切换到相应用户，执行脚本， 当缺少with grant option时， 将视图赋权给其他用户的时候，会产生错误。

P.S.

ORA-01720: grant option does not exist 的产生原因/条件 （不考虑sys权限）

1. 赋权的对象是一个视图 
2. 该视图里用到的基础的表属于第三个用户

references: https://logic.edchen.org/how-to-resolve-ora-01720-grant-option-does-not-exist/

