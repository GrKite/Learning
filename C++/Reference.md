# References in C++

When a variable is declared as a reference, it becomes an alternative name  for an existing variable. A variable can be declared as a reference by  putting ‘&’ in the declaration. 



```c++
#include<iostream>
using namespace std;
  
int main()
{
  int x = 10;
  
  // ref is a reference to x.
  int& ref = x;
  
  // Value of x is now changed to 20
  ref = 20;
  cout << "x = " << x << endl ;
  
  // Value of x is now changed to 30
  x = 30;
  cout << "ref = " << ref << endl ;
  
  return 0;
}
```



**Comments**

a reference is just an alternative name for the existing variable. That is a really nice explanation. 

It means the reference and the variable is the same thing ;)



**To be mentioned**

the reference in the function parameters, this situation is needed to pay attention to





本例中，变量 b 就是变量 a 的引用，它们用来指代同一份数据；也可以说变量 b 是变量 a 的另一个名字。从输出结果可以看出，a 和 b 的地址一样，都是`0x28ff44`；或者说地址为`0x28ff44`的内存有两个名字，a 和 b，想要访问该内存上的数据时，使用哪个名字都行



e.g.

```c++
#include <iostream>
using namespace std;
 
struct Person
{
    int id;
    char name[20];
};


int main()
{

    Person p1 = 
    {
        1, "kkk"
    };

    Person & pr1 = p1;
    cout << pr1.id << ":" << pr1.name << endl; // 引用就是一个别名, 突然记起来了

    return 0;
}
```

> reference is the alternative name of the variable, so we can use the `.` like the original variable itself.
