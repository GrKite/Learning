```c++
#pragma warning( disable : 4996) 
#include <cstring>
using namespace std;
```

意义很简单，就是告诉你，strcpy()函数不安全，必须改为使用strcpy_s()函数，首先不管改成strcpy_s()函数之后会发生什么后续问题，其实从理论上来说，上面的代码语法上和逻辑上来说都是对的，那么怎么避免编辑器强制要求你使用安全版本呢？

其实解决方法有很多，单单是避免上图中的错误代码4996的情况，可以使用编辑器的选择性提供warning功能，在include语句前面加上下句：
————————————————
版权声明：本文为CSDN博主「Leonardo Liu」的原创文章，遵循CC 4.0 BY-SA版权协议，转载请附上原文出处链接及本声明。
原文链接：https://blog.csdn.net/leowinbow/article/details/82380252