![[Base/1/3/1/img1.png]]
![[Base/1/3/1/img2.png]]
![[Base/1/3/1/img3.png]]
![[Base/1/3/1/img4.png]]
```cpp
int age = 13;

if (age >= 18)
{
    cout << "Здравствуйте, Алексей!";
}
else
{
    cout << "Привет, Алёша.";
}
```
![[Base/1/3/1/img5.png]]
```cpp
#include <iostream>
using namespace std;

int main()
{
    const int CODE = 1928;
    int a;
    cin >> a;

    // Здесь будет твой код . . .
    if (a == CODE) { cout << "Доступ получен" << endl; }
    else { cout << "Нет доступа" << endl; }
}
```
![[Base/1/3/1/img6.png]]
```cpp
#include <iostream>
#include <cmath>
using namespace std;

int main()
{
    int a, b;
    int res; // Переменная для ответа

    cin >> a;
    cin >> b;
    res = max(a, b);

    // Здесь будет твой код . . . 

    cout << "Скорость быстрейшего бегуна: " << res;
}
```
![[Base/1/3/1/img7.png]]
```cpp
#include <iostream>
using namespace std;

int main()
{
    // Здесь будет твой код . . . 
    int a;
    cin >> a;
    
    if (a % 2 == 0) { cout << "Чётное" << endl; }
    else { cout << "Нечётное" << endl; }
}
```
![[img8.png]]
```cpp
#include <iostream>
using namespace std;

int main()
{
    // Здесь будет твой код . . . 
    float a, b;
    cin >> a;
    cin >> b;
    
    if (b == 0) { cout << "На ноль делить нельзя" << endl; }
    else { cout << a / b << endl; }
}
```