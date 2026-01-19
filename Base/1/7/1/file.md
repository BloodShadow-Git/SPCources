![[Base/1/7/1/img1.png]]
```cpp
#include <iostream>
using namespace std;

// ↓ Определи здесь функцию my_own_func ↓

void my_own_func() {
    cout << "С Новым годом, господа!" << endl;
}

int main()
{
    // Вызов функции 3 раза (не изменяй это)
    my_own_func();
    my_own_func();
    my_own_func();
}
```
![[Base/1/7/1/img2.png]]
```cpp
#include <iostream>
using namespace std;

// ↓ Напиши здесь обе функции ↓

void stars() { cout << string(7, '*') << endl; }

void body() { cout << '*' << string(5, ' ') << '*' << endl; }

int main()
{
    // Вызовы функций (не изменяй это)
    stars();
    body();
    body();
    body();
    stars();
}
```
![[Base/1/7/1/img3.png]]
```cpp
#include <iostream>
using namespace std;

// ↓ Определи здесь эту функцию ↓

void happy_new_year(int i) { cout << "С новым " << i << " годом!" << endl; }

int main()
{
    // Вызов функции (не изменяй это)
    for (int i = 2023; i <= 2025; ++i)
    {
        happy_new_year(i);
    }
}
```
![[Base/1/7/1/img4.png]]
```cpp
#include <iostream>
#include <string>
using namespace std;

// ↓ Определи здесь функцию hello ↓
void hello(string n) { cout << "Привет, " << n << '!' << endl; }


int main()
{
    string name;
    cin >> name;

    // Вызов функции (не изменяй это)
    hello(name);
}
```
![[Base/1/7/1/img5.png]]
```cpp
#include <iostream>
using namespace std;

// ↓ Определи здесь функцию avg ↓
void avg(float a, float b, float c) { cout << (a + b + c) / 3 << endl; }


int main()
{
    float a, b, c;
    cin >> a >> b >> c;

    // Вызов функции (не изменяй это)
    avg(a, b, c);
}
```