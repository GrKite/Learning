#### const指针

```c
#include <stdio.h>

int main()
{
	int n = 1;
	const int* p = &n;
	int b = *p;
//	*p = 11; // 该块内存只能读不能写 // assignment of read-only location '*pA' 
	
	return 0;
}
```

- 所以const的作用是封禁（限制）*（星号操作）里的写内存功能

- 称为只读的，ReadOnly,  这块内存只能读， 不能写

  

  

  #### const指针用途

  const用于限定函数的参数

  ```c
  int avg(const int* p, int len)
  {
      
  }
  ```

  用于显式地指定: 该函数是输入参数, 在函数里只是读取这一个内存, 而不会修改这个内存的值.

  

  当不需要修改内存的时候, 在指针前面加上const修饰, 避免一些误操作.

  

  

  ##### const指针： 注意事项

  const只是封禁的是星号操作， 不允许写内存

  但是对于普通的加减法是没有关系的

  ```c
  #include <stdio.h>
  
  void test(const int* p, int len)
  {
  	for(int i = 0; i < len; i++)
  	{
  		printf("%d\n", *p);
  		p += 1;
  	}
  }
  
  int main()
  {
  	int arr[4] = {1, 2, 3, 4};
  	printf("sizeof arr = %d\n", sizeof(arr));
  	int len = sizeof(arr) / sizeof(arr[0]);
  	test(arr, len);
  	getchar();
  	return 0;
  }
  
  ```

  

  

  ##### 一个不常用的语法

  - 以下知识点仅在考试中可能遇到， 实际工程中基本不会用到。
  
    ```c
    int a;
    int b;
    int* const p = &a; // 这是另一种语法 
    // 这种语法的话, 是不能更改指针所指的东西的说
    // assignment of read-only variable 'pC', 指针不能更改, 该指针本身的读写操作不受影响
    
    
    ```
    
    const 封禁的是p, p不能改变, 但是该指针做相应的读写内存操作不受影响
  
  
  
  ```c
  #include <stdio.h>
  
  int main()
  {
      // const int*
      int a = 10;
      int b = 12;
      const int* pA = &a;
      printf("a = %d\n", *pA);
      //*pA = 11; //  error: assignment of read-only location '*pA'
      pA = &b;
      printf("b = %d\n", *pA);
  
      // int const*
      int const* pB = &a;
      printf("pB --> a = %d\n", *pB);
      //*pB = 15; //  error: assignment of read-only location '*pB'
      pB = &b;
  
      // int* const
      int* const pC = &a;
      printf("pC --> a = %d\n", *pC);
      *pC = 13;
      printf("pC1 --> a = %d\n", *pC);
      //pC = &b; // error: assignment of read-only variable 'pC'
  
      return 0;
  }
  ```
  
  
  
  ###### 内存区段错误（英语：Segmentation fault，经常被缩写为 segfault）
  
  

