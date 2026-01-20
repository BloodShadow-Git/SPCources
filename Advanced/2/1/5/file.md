![[Advanced/2/1/5/img1.png]]
![[Advanced/2/1/5/img2.png]]
```cpp
//typedef ComplexFunction
typedef int (*FuncFromDouble)(double);
typedef int* (*FuncFromConstChar)(char const*);
typedef FuncFromConstChar (*ComplexFunction)(int, FuncFromDouble);
```