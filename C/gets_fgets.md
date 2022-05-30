https://www.geeksforgeeks.org/fgets-gets-c-language/

```c
#include <stdio.h>
#define MAX 15

// fgets() is safe, but gets() is not that safe ;)
int main(void)
{
    char buf[MAX];
    printf("Enter a string:");
    //fgets(buf, MAX, stdin);
    gets(buf);
    printf("string is %s\n", buf);

    return 0;
}
```

fgets() is safe, but gets() is not that safe ;)