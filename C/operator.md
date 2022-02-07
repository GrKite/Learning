```c
#include <stdio.h>

int main(void)
{
    int num = 100;

    int ret = 1 <= num;
    printf("ret = %d\n", ret);
    if(1 <= num && num <= 20)
    {
        printf("kkkk\n");
    }
    return 0;
}
```

-- about the compare operator: equal or greater than >=

` 1 <= num <= 20` ,  this is viewed as the result  of `1 <= num`  is `1`, the  result of `1 <= 20` is true, so even if  `num = 100`, the equation `1 <= num <= 20`, is still true and the program can execute next fluently.