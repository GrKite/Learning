# Destructor

析构函数(Destructor) 也是一种特殊的成员函数, 没有返回值, 不需要程序员显式调用(程序员也没法显式调用), 而是在销毁对象的时自动执行. 构造函数的名字和类名相同, 而析构函数的名字是在类名前面加一个 **~** 符号.



注意: 析构函数没有参数, 不能被重载, 因此一个类只能有一个析构函数. 如果用户没有定义, 编译器会自动生成一个默认的析构函数.



创建对象时, 系统会自动调用构造函数进行初始化工作, 同样, 销毁对象时系统也会自动调用一个函数来进行清理工作, 例如释放分配的内存, 关闭打开的文件等, 这个函数就是析构函数.



- Tips:

  know the time of the executing of the Destructor 

  practice the new and delete thing

  leetcode / C-exercise everyday

  learn the C lesson daily

  