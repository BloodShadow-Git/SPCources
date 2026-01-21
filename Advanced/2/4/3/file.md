![[Advanced/2/4/3/img1.png]]
![[Advanced/2/4/3/img2.png]]
```cpp
#include <utility> // std::declval
#include <type_traits> // std::is_nothrow_...

// внутри do_math объекты типа T
// - копируются
// - присваиваются
// - складываются оператором +
template<class T>
void do_math() noexcept(
    std::is_nothrow_copy_constructible<T>::value &&
    std::is_nothrow_copy_assignable<T>::value &&
    noexcept(std::declval<T>() + std::declval<T>())
)
{
    // тело функции нужно оставить пустым
}
```
![[Advanced/2/4/3/img3.png]]
```cpp
#include <utility> // std::declval

template<class T>
void do_math() noexcept(
    noexcept(T(std::declval<const T&>())) &&                // конструктор копирования
    noexcept(T(std::declval<T&&>())) &&                     // конструктор перемещения (опционально)
    noexcept(std::declval<T&>() = std::declval<const T&>()) && // копирующее присваивание
    noexcept(std::declval<T&>() = std::declval<T&&>()) &&   // перемещающее присваивание (опционально)
    noexcept(std::declval<T>() + std::declval<T>())         // оператор +
)
{
    // тело функции нужно оставить пустым
}
```