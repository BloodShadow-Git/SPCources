![[Base/1/3/3/img1.png]]
```cpp
int hours = 15;

if (!(hours <= 18))
{
    cout << "Вечер";
}
else if (hours > 12)
{
    cout << "День";
}
else if (hours > 6)
{
    cout << "Утро";
}
else
{
    cout << "Ночь";
}
```
![[Base/1/3/3/img2.png]]
```cpp
#include <iostream>
using namespace std;

int main()
{
    // Здесь будет твой код . . . 
    int a;
    cin >> a;
    if (a <= 0) { cout << "Лёд" << endl; }
    else if (a < 100) { cout << "Жидкая вода" << endl; }
    else { cout << "Водяной пар" << endl; }
}
```
![[Base/1/3/3/img3.png]]
```cpp
#include <iostream>
using namespace std;

int main()
{
    // Здесь будет твой код . . . 
    int a, b;
    cin >> a >> b;
    
    if (a > b) { cout << "Победит Деннис" << endl; }
    else if (a == b) { cout << "Победит дружба" << endl; }
    else { cout << "Победит Бьёрн" << endl; }
}
```
![[Base/1/3/3/img4.png]]
```cpp
int number;
cin >> number;

switch (number)
{
case 1:
    cout << "Этот горячее льда";
    break;
case 2:
    cout << "Этому не нужно знание";
    break;
case 13:
    cout << "Этот любит поиграть";
    break;
case 0:
    cout << "Этот вот загадочен уж очень";
    break;
default:
    cout << "А этот мне вовсе неизвестен...";
}
```
![[Base/1/3/3/img5.png]]
```cpp
#include <iostream>
using namespace std;

int main()
{
    int day;
    cin >> day;

    switch (day)
    {
        case 1:
            cout << "понедельник" << endl;
            break;
        case 2:
            cout << "вторник" << endl;
            break;
        case 3:
            cout << "среда" << endl;
            break;
        case 4:
            cout << "четверг" << endl;
            break;
        case 5:
            cout << "пятница" << endl;
            break;
        case 6:
            cout << "суббота" << endl;
            break;
        case 7:
            cout << "воскресенье" << endl;
            break;
    }
}
```
![[Base/1/3/3/img6.png]]
```cpp
#include <iostream>
using namespace std;

int main()
{
    int a;
    cin >> a;
    
    switch (a)
    {
        case 1:        
        case 2:
        case 12:
            cout << "зима" << endl;
            break;
        case 3:        
        case 4:
        case 5:
            cout << "весна" << endl;
            break;
        case 6:        
        case 7:
        case 8:
            cout << "лето" << endl;
            break;
        case 9:        
        case 10:
        case 11:
            cout << "осень" << endl;
            break;
        default:
            cout << "Нет такого месяца" << endl;
            break;
    }
}
```
![[Base/1/3/3/img7.png]]
```cpp
#include <iostream>
using namespace std;

int main()
{
    char op;
    float a, b;

    cin >> a; // Левое число
    cin >> op; // Знак операции
    cin >> b; // Правое число

    switch (op)
    {
    case '+':
        cout << a + b; 
        break;            
    case '-':
        cout << a - b; 
        break;            
    case '*':
        cout << a * b; 
        break;            
    case '/':
            if (b == 0) { cout << "На ноль делить нельзя"; }
            else { cout << a / b; }
        break;
    }
}
```