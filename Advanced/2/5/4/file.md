![[Advanced/2/5/4/img1.png]]
```cpp
#include <type_traits>
#include <string>

// Вспомогательный шаблон для SFINAE
template<typename T>
auto get_size_impl(const T& value, int) -> decltype(value.size(), size_t()) {
    // Вызывается, если есть метод size()
    return value.size();
}

template<typename T>
auto get_size_impl(const T& value, ...) -> decltype(T::size, size_t()) {
    // Вызывается, если есть поле size
    return value.size;
}

// Главная функция
template<typename T>
size_t get_size(const T& value) {
    return get_size_impl(value, 0);
}
```