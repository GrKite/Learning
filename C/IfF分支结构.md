e.g.

```c
#include <stdio.h>

int main(void)
{
    int a = 10;
    if(a >= 1)
    {
        printf("a >= 1\n");
    }
    else if(a >= 2)
    {
         printf("a >= 2\n");
    }
    else if(a >= 3)
    {
         printf("a >= 3\n");
    }

    printf("Done!\n");

    return 0;
}
```

if语句的话， 从上到下依次检测判断条件，当某个判断条件成立时，则执行其对应的语句块，然后跳到整个 if else 语句之外继续执行其他代码。

如果所有判断条件都不成立，则执行语句块n，然后继续执行后续代码。

也就是说，一旦遇到能够成立的判断条件，则不再执行其他的语句块，所以最终只能有一个语句块被执行。



```c
if(判断条件1){
    语句块1
} else  if(判断条件2){
    语句块2
}else  if(判断条件3){
    语句块3
}else  if(判断条件m){
    语句块m
}else{
     语句块n
}
```

