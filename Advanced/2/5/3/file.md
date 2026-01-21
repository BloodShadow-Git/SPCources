![[Advanced/2/5/3/img1.png]]
```cpp
#include <iostream>
#include <type_traits>

template <unsigned N>
struct Fib {
    static constexpr unsigned long long value = 
        Fib<N - 1>::value + Fib<N - 2>::value;
};

template <>
struct Fib<0> {
    static constexpr unsigned long long value = 0;
};

template <>
struct Fib<1> {
    static constexpr unsigned long long value = 1;
};

// Альтернатива: constexpr функция для вычисления во время компиляции
constexpr unsigned long long fib_constexpr(unsigned n) {
    return n <= 1 ? n : fib_constexpr(n - 1) + fib_constexpr(n - 2);
}
```
![[Advanced/2/5/3/img2.png]]
```cpp
template<int...>
struct IntList;

// Базовый шаблон для пустого списка
template<>
struct IntList<> {
    static constexpr int Head = 0; // или можно генерировать ошибку
};

// Специализация для непустого списка
template<int HeadValue, int... TailValues>
struct IntList<HeadValue, TailValues...> {
    static constexpr int Head = HeadValue;
    using Tail = IntList<TailValues...>;
};
```
![[Advanced/2/5/3/img3.png]]
```cpp
// Метафункция Length - общая версия
template<typename List>
struct Length {
    static constexpr size_t value = 0;
};

// Специализация для непустого списка
template<template<int...> class List, int Head, int... Tail>
struct Length<List<Head, Tail...>> {
    static constexpr size_t value = 1 + Length<List<Tail...>>::value;
};
```
![[Advanced/2/5/3/img4.png]]
```cpp
#include <type_traits>

template<int N, typename List>
struct IntCons;

template<int N, int... Values>
struct IntCons<N, IntList<Values...>> {
    using type = IntList<N, Values...>;
};

template<int N, typename List = IntList<>>
struct Generate;

// Базовый случай
template<int... Values>
struct Generate<0, IntList<Values...>> {
    using type = IntList<Values...>;
};

// Рекурсивный случай
template<int N, int... Values>
struct Generate<N, IntList<Values...>> {
    using type = typename Generate<N-1, IntList<N-1, Values...>>::type;
};
```
![[Advanced/2/5/3/img5.png]]
```cpp
#include <tuple>
#include <utility>

// IntList - список целых чисел в виде типа
template<int...>
struct IntList {};

// Генерация последовательности 0..N-1 (новое имя)
template<int N, int... Is>
struct GenerateSequence : GenerateSequence<N-1, N-1, Is...> {};

template<int... Is>
struct GenerateSequence<0, Is...> {
    using type = IntList<Is...>;
};

// Вспомогательная функция apply_impl
template<typename F, typename Tuple, int... Is>
auto apply_impl(F&& f, Tuple&& t, IntList<Is...>) ->
    decltype(std::forward<F>(f)(std::get<Is>(std::forward<Tuple>(t))...)) {
    return std::forward<F>(f)(std::get<Is>(std::forward<Tuple>(t))...);
}

// Основная функция apply
template<typename F, typename Tuple>
auto apply(F&& f, Tuple&& t) ->
    decltype(apply_impl(std::forward<F>(f), std::forward<Tuple>(t),
                        typename GenerateSequence<std::tuple_size<typename std::decay<Tuple>::type>::value>::type())) {
    using Indices = typename GenerateSequence<std::tuple_size<typename std::decay<Tuple>::type>::value>::type;
    return apply_impl(std::forward<F>(f), std::forward<Tuple>(t), Indices());
}
```
![[Advanced/2/5/3/img6.png]]
```cpp
// Предполагаем, что IntList и IntCons уже определены следующим образом:
template<int... Values>
struct IntList;

template<int H, typename T>
struct IntCons;

// Бинарная метафункция Plus для примера
template<int a, int b>
struct Plus
{
    static int const value = a + b;
};

// Основная метафункция Zip
template<typename List1, typename List2, template<int, int> class Func>
struct Zip;

// Частичная специализация для пустых списков
template<template<int, int> class Func>
struct Zip<IntList<>, IntList<>, Func>
{
    using type = IntList<>;
};

// Частичная специализация для непустых списков
template<int Head1, int... Tail1, int Head2, int... Tail2, template<int, int> class Func>
struct Zip<IntList<Head1, Tail1...>, IntList<Head2, Tail2...>, Func>
{
    // Вычисляем значение для текущих головных элементов
    static constexpr int current = Func<Head1, Head2>::value;
    
    // Рекурсивно обрабатываем хвосты
    using rest = typename Zip<IntList<Tail1...>, IntList<Tail2...>, Func>::type;
    
    // Собираем результат
    using type = typename IntCons<current, rest>::type;
};
```
![[Advanced/2/5/3/img7.png]]
```cpp
#include <type_traits>
#include <stdexcept>
#include <cmath>

// Минимальные определения для компиляции
template<int... vals>
struct IntList {};

// Zip для сложения размерностей
template<typename L1, typename L2> 
struct ZipAdd;

template<int... vals1, int... vals2>
struct ZipAdd<IntList<vals1...>, IntList<vals2...>> {
    using type = IntList<(vals1 + vals2)...>;
};

// Zip для вычитания размерностей
template<typename L1, typename L2> 
struct ZipSub;

template<int... vals1, int... vals2>
struct ZipSub<IntList<vals1...>, IntList<vals2...>> {
    using type = IntList<(vals1 - vals2)...>;
};

// Сравнение списков
template<typename L1, typename L2>
struct ListsEqual;

template<int... vals1, int... vals2>
struct ListsEqual<IntList<vals1...>, IntList<vals2...>> {
    static const bool value = std::is_same<IntList<vals1...>, IntList<vals2...>>::value;
};

// Класс Quantity
template<typename Dim>
class Quantity {
private:
    double val_;
    
public:
    // Конструктор по умолчанию
    Quantity() : val_(0.0) {}
    
    // explicit конструктор от double
    explicit Quantity(double v) : val_(v) {}
    
    // Метод value()
    double value() const { return val_; }
    
    // Сложение (только одинаковые размерности)
    template<typename OtherDim>
    typename std::enable_if<ListsEqual<Dim, OtherDim>::value, Quantity>::type
    operator+(const Quantity<OtherDim>& other) const {
        return Quantity(val_ + other.value());
    }
    
    // Вычитание (только одинаковые размерности)
    template<typename OtherDim>
    typename std::enable_if<ListsEqual<Dim, OtherDim>::value, Quantity>::type
    operator-(const Quantity<OtherDim>& other) const {
        return Quantity(val_ - other.value());
    }
    
    // Умножение величин
    template<typename OtherDim>
    Quantity<typename ZipAdd<Dim, OtherDim>::type> 
    operator*(const Quantity<OtherDim>& other) const {
        using ResultDim = typename ZipAdd<Dim, OtherDim>::type;
        return Quantity<ResultDim>(val_ * other.value());
    }
    
    // Деление величин
    template<typename OtherDim>
    Quantity<typename ZipSub<Dim, OtherDim>::type>
    operator/(const Quantity<OtherDim>& other) const {
        using ResultDim = typename ZipSub<Dim, OtherDim>::type;
        return Quantity<ResultDim>(val_ / other.value());
    }
    
    // Умножение на число
    Quantity operator*(double scalar) const {
        return Quantity(val_ * scalar);
    }
    
    // Деление на число
    Quantity operator/(double scalar) const {
        if (std::abs(scalar) < 1e-15) {
            throw std::runtime_error("Division by zero");
        }
        return Quantity(val_ / scalar);
    }
    
    // Дружественные функции для умножения числа на величину
    friend Quantity operator*(double scalar, const Quantity& q) {
        return Quantity(scalar * q.val_);
    }
};

// Умножение числа на величину (вне класса для любых типов)
template<typename Dim>
Quantity<Dim> operator*(double scalar, const Quantity<Dim>& q) {
    return Quantity<Dim>(scalar * q.value());
}

// Деление числа на величину
template<typename Dim>
Quantity<typename ZipSub<IntList<0,0,0,0,0,0,0>, Dim>::type>
operator/(double scalar, const Quantity<Dim>& q) {
    using ZeroDim = IntList<0,0,0,0,0,0,0>;
    using ResultDim = typename ZipSub<ZeroDim, Dim>::type;
    if (std::abs(q.value()) < 1e-15) {
        throw std::runtime_error("Division by zero");
    }
    return Quantity<ResultDim>(scalar / q.value());
}

// Определения размерностей из условия
template<int m = 0, int kg = 0, int s = 0, int A = 0, int K = 0, int mol = 0, int cd = 0>
using Dimension = IntList<m, kg, s, A, K, mol, cd>;

using NumberQ   = Quantity<Dimension<>>;
using LengthQ   = Quantity<Dimension<1>>;
using MassQ     = Quantity<Dimension<0, 1>>;
using TimeQ     = Quantity<Dimension<0, 0, 1>>;
using VelocityQ = Quantity<Dimension<1, 0, -1>>;
using AccelQ    = Quantity<Dimension<1, 0, -2>>;
using ForceQ    = Quantity<Dimension<1, 1, -2>>;
```