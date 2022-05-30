关于 CString的使用方式的说
```c++
#pragma warning( disable : 4996) 
#include <stdio.h>
#include <atlstr.h>
#include <string.h>

int main()
{
	CString a, b;
	a = "1234567";
	b = a.Left(4);
	b = a.Mid(3);
	a += "||";
	a += b;

	return 0;
}
```

