# extern

​         

```
#include <stdio.h>

int i=1;  // external variable, also can be written into    extern int i = 1;

int main()
{
    int i=2;            // local variable
    printf("%d\n", i);  // print local variable i==2

    {
    extern int i;       // point to external variable
    printf("%d\n", i);  // print external variable i==1
    }

    return 0;
}
```




Once you define a variable named `i` inside your `main` function, the `i` at file scope is masked and cannot be accessed (unless you have its address).

When you later add the declaration `extern int i`, this conflicts with the local variable named `i` at the same scope since locals can't have external linkage.  It does **not** give you access to the global `i`.

When you remove the local `i`, the `extern int i` declaration matches up with the definition at file scope, so there is no error.  As for the warning on `extern int i=1;`, that did *not* go away for me on gcc 4.1.2, so that depends on the compiler      

                     Re “locals can't have  external linkage”: Linkage is a property of identifiers, and identifiers in block scope certainly can have external linkage. The reason `int i=2; extern int i;` has a conflict is C 2018 (and 2011 and earlier) 6.7 3 gives the constraint that, if an identifier has no linkage (which the `i` in `int i=2;` satisfies), there shall be no more than one declaration of it in the  same scope and namespace, with certain exceptions for typedef names and  tags.



There are two main reasons we can use *extern* keyword in C:
 \1. When we want to declare a variable explicitly/globally but without its definition.
 \2. To make the variable globally visible from any other file in a  multi-file program or other location of the same file (see Ihdina's  exmaple for this scenario).



tips:

```
extern int i = 2; // it equals to the int i = 2; and it is a definition
extern 意味着向外求一个具有相关属性的变量, 一般就是全局变量吧? 局部变量的话, 就会产生问题, 局部变量没有external linkage.
```

> reference: https://stackoverflow.com/questions/45724358/error-extern-declaration-of-i-follows-declaration-with-no-linkage



