virtual function:
```c++
#include <iostream>
using namespace std;

class Parent
{
    public:
        char data[20];
        void Function1();
        virtual void Function2(); // here Function2 is virtual function
} parent;

void Parent::Function1()
{
    printf("This is parent, function1\n");
}

void Parent::Function2()
{
    printf("This is parent, function2\n");
}

class Child:public Parent
{
    void Function1();
    void Function2();
} child;

void Child::Function1()
{
    printf("This is child, function1\n");
}

void Child::Function2()
{
    printf("This is child, function2\n");
}

int main(int argc, const char* argv[])
{
    Parent *p; // define a basic pointer
    printf("Please enter a character:\n");

    if(getchar() == 'c')
    {
        p = &child; // point to inherited objects
    }
    else
    {
        p = &parent; // point to basic objects
    }

    p->Function1(); // here, when compiling, directly give the address of Parent::Function1
    p->Function2();

    return 0;
}
```

##### 虚函数最关键的特点是“动态联编”，它可以在运行时判断指针指向的对象，并自动调用相应的函数

输入一个小写字母c, 得到下面的结果:

```c
This is parent, function1
This is child, function2
```

为什么会有第一行的结果呢?

因为我们是用一个Parent类的指针调用函数Function1(), 虽然实际上这个指针指向的是Child类的对象, 但编译器无法知道这一事实(直到运行的时候, 程序才可以根据用户的输入判断出指针指向的对象), 它只能按照调用Parent类的函数来理解并编译, 所以我们看到了第一行的结果.

那么第二行的结果又是怎么回事呢? 我们注意到, Function2()函数在基类中被virtual关键字修饰, 也就是说, 它是一个虚函数.

**虚函数最关键的一个特点就是"动态联编", 它可以在运行时判断指针指向的对象, 并自动调用相应的函数.**

如果我们在运行上面的程序时任意输入一个非c的字符, 结果如下:

```c
This is parent, function1
This is parent, function2
```

请注意看第二行, 它的结果出现了变化. 程序中仅仅调用了一个Function2()函数, 却可以根据用户的输入自动决定到底调用基类中的Function2还是继承类中的Function2, 这就是虚函数的作用.

P.S.: **一定要注意"静态联编"和"动态联编"的区别**





