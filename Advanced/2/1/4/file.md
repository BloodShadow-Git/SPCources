![[Advanced/2/1/4/img1.png]]
```cpp
#include <typeinfo>

bool check_equals(Expression const *left, Expression const *right)
{
    return typeid(*left) == typeid(*right);
}
```
![[Advanced/2/1/4/img2.png]]
```cpp
#include <cstdint>
#include <cassert>

// возвращает true, если p и q указывают на один и тот же объект
template<class T>
bool isSameObject(T const * p, T const * q)
{
    // Если оба указателя nullptr или один из них nullptr
    if (p == q) {
        return true;
    }
    if (p == nullptr || q == nullptr) {
        return false;
    }
    
    // Преобразуем к void* через dynamic_cast для полиморфных типов
    // или через reinterpret_cast для неполиморфных типов
    const void* vp = dynamic_cast<const void*>(p);
    const void* vq = dynamic_cast<const void*>(q);
    
    // Если dynamic_cast работает (тип полиморфный)
    if (vp != nullptr && vq != nullptr) {
        return vp == vq;
    }
    
    // Для неполиморфных типов используем reinterpret_cast
    // (хотя в условии сказано про полиморфные классы)
    return reinterpret_cast<const void*>(p) == reinterpret_cast<const void*>(q);
}
```