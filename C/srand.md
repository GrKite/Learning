srand 函数是随机数发生器的初始化函数。

原型:

```
void srand(unsigned seed);
```

**用法:** 它初始化随机种子，会提供一个种子，这个种子会对应一个随机数，如果使用相同的种子后面的 rand() 函数会出现一样的随机数，如: srand(1); 直接使用 1 来初始化种子。不过为了防止随机数每次重复，常常使用系统时间来初始化，即使用 time函数来获得系统时间，它的返回值为从 00:00:00 GMT, January 1, 1970 到现在所持续的秒数，然后将time_t型数据转化为(unsigned)型再传给srand函数，即: srand((unsigned) time(&t)); 还有一个经常用法，不需要定义time_t型t变量,即: srand((unsigned) time(NULL)); 直接传入一个空指针，因为你的程序中往往并不需要经过参数获得的数据。

**进一步说明下：**计算机并不能产生真正的随机数，而是已经编写好的一些无规则排列的数字存储在电脑里，把这些数字划分为若干相等的N份，并为每份加上一个编号用srand()函数获取这个编号，然后rand()就按顺序获取这些数字，当srand()的参数值固定的时候，rand()获得的数也是固定的，所以一般srand的参数用time(NULL)，因为系统的时间一直在变，所以rand()获得的数，也就一直在变，相当于是随机数了。只要用户或第三方不设置随机种子，那么在默认情况下随机种子来自系统时钟。如果想在一个程序中生成随机数序列，需要至多在生成随机数之前设置一次随机种子。

 **即：**只需在主程序开始处调用 srand((unsigned)time(NULL)); 后面直接用rand就可以了。不要在 for 等循环放置 srand((unsigned)time(NULL));

```
void test_rand(void)
    {
    unsigned long n;
    srand((unsigned)time(NULL));
    for(int i = 0; i < 100; i++)
    {
        n = rand();
        printf("d\n", n);
    }
}
```