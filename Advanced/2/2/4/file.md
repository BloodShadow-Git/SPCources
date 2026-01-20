![[Advanced/2/2/4/img1.png]]
![[Advanced/2/2/4/img2.png]]
```cpp
#include <utility> // для std::move и std::forward

// реализация функции apply
template<typename F, typename... Args>
auto apply(F&& f, Args&&... args) -> decltype(f(std::forward<Args>(args)...))
{
    return f(std::forward<Args>(args)...);
}
```