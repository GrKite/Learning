F5进行调试







![image-20211222090253842](C:\Users\duoduo.liu\AppData\Roaming\Typora\typora-user-images\image-20211222090253842.png)

绿色箭头表示， 从第17行返回后， 函数栈发生异常。

结论：当变量体积太大是， 应该用malloc或new来动态分配内存。

会导致函数栈溢出的另一种原因： 函数递归调用， 层次太深， 没有终止条件。





#### 3.4 指针的目标对象不可用

指针指向的对象（内存）必须保证是有效的、可以访问的。

分一下几种情况：

（1）空指针

（2）野指针

		- 指针未赋值
		- free/delete释放了的对象又去使用
		- 不恰当的指针强制转换





(1) 空指针

0x00000000 这个就是空指针， NULL

![image-20211222093554700](C:\Users\duoduo.liu\AppData\Roaming\Typora\typora-user-images\image-20211222093554700.png)

可以在调用堆栈查看是什么传递了空指针过去





![image-20211222093940080](C:\Users\duoduo.liu\AppData\Roaming\Typora\typora-user-images\image-20211222093940080.png)

绿色箭头的地方， 表示该处调用了show(obj), 这里obj为NULL, 可以直接查看相应的变量的值 



（2）野指针

  - 指针未赋值					
  - free/delete释放了的对象又去使用 			// free之后就不能使用了， 因为变成了野指针了哇
  - 不恰当的指针强制转换





- 不恰当的指针强制转换

```c
#include <stdio.h>

int main()
{
	int a = 10;
	double* p = (double*) &a; // 可以将一个int * 转换成 double *, 但没有实际意义， 使用的时候会报错
	*p = 123.345; // <-- 程序崩溃

	return 0;
}
```



指针强制转换时， 必须要对它有足够的理解才能使用。