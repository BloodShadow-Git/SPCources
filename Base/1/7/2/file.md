![[Base/1/7/2/img1.png]]
```cpp
#include <iostream>
using namespace std;

// ↓ Напиши здесь функцию to_celsius ↓

float to_celsius(float fah) {
    return (fah - 32) * (5.0 / 9.0);
}

int main()
{
    float fah;
    cin >> fah;

    // Вызов функции (не трогать)
    cout << to_celsius(fah);
}
```
![[Base/1/7/2/img2.png]]
```cpp
#include <iostream>
// Как же та библиотека называлась?
#include <cmath>
using namespace std;

// ↓ Определи здесь функцию geom_mean ↓
float geom_mean(float a, float b){
    return sqrt(a * b);
}


int main()
{
    float a, b;
    cin >> a;
    cin >> b;

    // Вызов функции (не изменяй это)
    cout << geom_mean(a, b);
}
```
![[Base/1/7/2/img3.png]]
```cpp
#include <iostream>
using namespace std;

// ↓ Напиши здесь функцию get_days ↓
int get_days(int m) {
    int days[12] = { 31, 28, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31 };
    return days[m - 1];
}


int main()
{
    int month;
    cin >> month;

    // Вызов функции (не трогай это)
    cout << get_days(month);
}
```
![[Base/1/7/2/img4.png]]
```cpp
#include <iostream>
using namespace std;

// ↓ Вот твоя функция ↓
bool is_leap_year(int a)
{
    return a % 4 == 0 && a % 100 != 0 || a % 400 == 0;
}

int main()
{
    int year;
    cin >> year;

    // Вызов функции (не изменяй это)
    if (is_leap_year(year)) {
        cout << "Yes";
    }
    else {
        cout << "No";
    }
}
```
![[Base/1/7/2/img5.png]]
```cpp
#include <iostream>
using namespace std;

// ↓ Напиши здесь функцию is_valid_triangle ↓
bool is_valid_triangle(int a, int b, int c){
    return a + b > c && b + c > a && c + a > b;
}


int main()
{
    int a, b, c;
    cin >> a >> b >> c;

    // Вызов функции (не изменяй это)
    if (is_valid_triangle(a, b, c)) {
        cout << "Yes";
    }
    else {
        cout << "No";
    }
}
```