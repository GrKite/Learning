public static member constant

<string>

# std::[string](https://www.cplusplus.com/reference/string/string/)::npos

```
static const size_t npos = -1;
```

Maximum value for size_t

`npos` is a static member constant value with the greatest possible value for an element of type [size_t](https://www.cplusplus.com/size_t).

 This value, when used as the value for a *len* (or *sublen*) parameter in [string](https://www.cplusplus.com/string)'s member functions, means *"until the end of the string"*.

 As a return value, it is usually used to indicate no matches.

 This constant is defined with a value of `-1`, which because [size_t](https://www.cplusplus.com/size_t) is an unsigned integral type, it is the largest possible representable value for this type.

