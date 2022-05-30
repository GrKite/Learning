https://www.javatpoint.com/c-gets-puts



some general points of function puts()



```c
#include <stdio.h>
#define MAX 50

int main(void)
{
    char name[MAX];
    printf("Please enter the name:");

    fgets(name, MAX, stdin);
    puts("====================");
    printf("the name is: ");
    puts(name);

    return 0;
}
```

