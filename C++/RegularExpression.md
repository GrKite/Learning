#### Regular Expression

e.g.

```c++
#include <iostream>
#include <string>
#include <regex> // use it for regular expression
using namespace std;

int main () 
{
    string text ( "software" ) ;
    regex str_expr ( "(soft)(.*)" ) ; // for regular expression 
    
    smatch sm ;  // for catching the desired matched
    regex_match ( text ,sm , str_expr ) ;
    
    cout << "String:range, size:" << sm.size() << " are the matches\n" ;
    cout << "The total matches are : " ;
    for ( int i = 1 ; i < sm.size() ; ++i ) // the first one is the matched part, not the whole, but the partition. the zero is the whole ;)
    {
        cout << "[" << sm.str(i) << "] " ;
    }
    cout << endl ;
    
    return 0 ;
}
```



tips:

1. 头文件`<regex>` , `#include <regex>`, 可以使用正则表达式

2. 使用捕获: `smatch sm;`

   	1) 第0个元素总是整体元素

   

references:
	https://www.cnblogs.com/hesse-summer/p/10875487.html#%E6%8D%95%E8%8E%B7  (Chinese edition, maybe more detailed)

​	https://www.educba.com/regular-expressions-in-c-plus-plus/  (English edition, nice examples)

   ​	