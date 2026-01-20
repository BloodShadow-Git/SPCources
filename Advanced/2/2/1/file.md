![[Advanced/2/2/1/img1.png]]
![[Advanced/2/2/1/img2.png]]
![[Advanced/2/2/1/img3.png]]
![[Advanced/2/2/1/img4.png]]
```cpp
#include <iostream>
#include <typeinfo>

void print_values(std::ostream& os) {
}

template<typename T, typename... Args>
void print_values(std::ostream& os, T first, Args... args) {
    os << typeid(first).name() << ": " << first;
    
    if (sizeof...(args) > 0) {
        os << std::endl;
    }
    
    print_values(os, args...);
}
```