# Dynamic memory allocation

- new

  - new int;
  - new Stash;
  - new int[10];

  new 做的事情: 分配空间; 如果是类的话, 还需要调用构造函数; 作为一个运算符, new也有结果, 结果是分配的地址

- delete

  - delete p;
  - delete [] p;

  delete就是释放空间, 析构函数先被调用, 析构完了之后再delete空间



# new and delete

- new is the way to allocate memory as a program runs. Pointers become the only access to that memory
- delete enables you to return memory to the memory pool when you are finished with it.



# Dynamic Arrays

```c++
int * psome = new int [10];
```

- The new operator returns the address of the first element of the block.

```c++
delete [] psome;
```

- The presence of the brackets tells the program that it should free the whole array, not just the element

[] 代表, 那么多个空间会被释放, 和那些空间所代表的析构都会被调用, 如果没有[], 那么多个空间会被释放, 但是只有第一个的析构函数会被调用. 

[] 代表有很多析构函数需要调用,

没有[]  代表只有那个地址上的一个析构函数需要调用



# The new-delete mech.

```c++
int * p = new int;
int * a = new int[10]; 
```

像这种程度的new的话, 就c++运行库里面申请了, 还不到操作系统里面的级别, 在程序运行的时候, 操作系统会分配空间, 像这样的程度的话, 直接可以在C++运行库里面申请空间.

![image-20220120110747821](C:\Users\duoduo.liu\AppData\Roaming\Typora\typora-user-images\image-20220120110747821.png)

还会有一个intra table记录下， 地址和分配的空间大小（以字节为单位）， 内部的数据表进行记录, 管理new 出来的东西



如果我们需要delete p, 就需要从inch table那边找一下有没有这个地址， 然后去delete;

如果我们需要delete q, 就需要从inch table那边找一下有没有这个地址， 然后去调用Student 的析构， 然后回收空间

如果我们需要delete r, 就需要从inch table那边找一下有没有这个地址， 然后去调用Student 的析构,  但是只调用一个，然后回收所有空间（回收空间只和table有关，析构和[]这个有关）

如果我们需要delete[] r, 就需要从inch table那边找一下有没有这个地址， 然后去调用全部的Student 的析构，然后回收所有空间（回收空间只和table有关，析构和[]这个有关）



![image-20220120111150355](C:\Users\duoduo.liu\AppData\Roaming\Typora\typora-user-images\image-20220120111150355.png)

e.g. delete p; // error occurs

```c++
A::A()
{
        printf("A::A()\n");
}

A::~A()
{
        printf("A::~A(), i = %d\n", i);
}

void A::set(int i)
{
        this->i = i;
}

int main()
{
        A* p = new A[10];       
        for(int i = 0; i < 10; i++)
        {
                p[i].set(i);
        }
        delete p;
        return 0;
}

```



```c++
[duoduo@localhost cc]$ ./a.out
A::A()
A::A()
A::A()
A::A()
A::A()
A::A()
A::A()
A::A()
A::A()
A::A()
A::~A(), i = 0
*** Error in `./a.out': munmap_chunk(): invalid pointer: 0x0000000002218018 ***
======= Backtrace: =========
/lib64/libc.so.6(+0x7f474)[0x7f4675afe474]
./a.out[0x4008e7]
/lib64/libc.so.6(__libc_start_main+0xf5)[0x7f4675aa1555]
./a.out[0x4006d9]
======= Memory map: ========
```

e.g.

 delete[] p;

```c++
A::A()
{
        printf("A::A()\n");
}

A::~A()
{
        printf("A::~A(), i = %d\n", i);
}

void A::set(int i)
{
        this->i = i;
}

int main()
{
        A* p = new A[10];       
        for(int i = 0; i < 10; i++)
        {
                p[i].set(i);
        }
        delete[] p;
        return 0;
}
```

```c++
[duoduo@localhost cc]$ ./a.out
A::A()
A::A()
A::A()
A::A()
A::A()
A::A()
A::A()
A::A()
A::A()
A::A()
A::~A(), i = 9
A::~A(), i = 8
A::~A(), i = 7
A::~A(), i = 6
A::~A(), i = 5
A::~A(), i = 4
A::~A(), i = 3
A::~A(), i = 2
A::~A(), i = 1
A::~A(), i = 0
```

# Tips for new and delete

- Do not use **delete** to free memory that **new** did not allocate.
- Do not use **delete** to free the same block of memory twice in succession.
- Use **delete[]** if you use **new []** to allocate an array.
- Use **delete** (no brackets) if you used **new** to allocate a single entity.
- It is safe to apply **delete** to the null pointer (nothing happens). // it is better if(p) delete p;



不去delete的话， 会存在内存泄漏Stack Overflow

