![[Advanced/2/2/3/img1.png]]
```cpp
#include <tuple>
#include <utility>

template<size_t I, size_t J, typename T>
std::pair<typename std::tuple_element<I, T>::type, typename std::tuple_element<J, T>::type>
to_pair(const T& tuple) {
    return std::make_pair(std::get<I>(tuple), std::get<J>(tuple));
}
```
![[Advanced/2/2/3/img2.png]]
```cpp
// определение структуры Point уже подключено
/* struct Point
{
    constexpr Point(double x, double y) 
        : x(x), y(y) 
    {}

    double x = 0;
    double y = 0;
};
*/

// сложение
constexpr Point operator+(const Point& a, const Point& b) 
{
    return Point(a.x + b.x, a.y + b.y);
}

// вычитание
constexpr Point operator-(const Point& a, const Point& b) 
{
    return Point(a.x - b.x, a.y - b.y);
}

// скалярное произведение
constexpr double operator*(const Point& a, const Point& b) 
{
    return a.x * b.x + a.y * b.y;
}
```
![[Advanced/2/2/3/img3.png]]
```cpp
// определение переменной
auto square_fun = [](int& x) { x = x * x; };
```
![[Advanced/2/2/3/img4.png]]
```cpp
// определение переменной
auto gen_finder = [](int *p, int *q) {
    return [p, q](int x) {
        return find_if(p, q, [x](int y){ return x == y; }) != q;
    };
};
```