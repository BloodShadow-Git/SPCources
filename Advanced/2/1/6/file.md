![[Advanced/2/1/6/img1.png]]
![[Advanced/2/1/6/img2.png]]
![[Advanced/2/1/6/img3.png]]
```cpp
#include <string>

template<typename T, typename R>
bool compare(const T& a, const T& b, R (T::*method)() const) {
    return (a.*method)() < (b.*method)();
}
```