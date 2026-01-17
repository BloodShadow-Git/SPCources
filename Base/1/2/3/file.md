![[Base/1/2/3/img1.png]]
![[Base/1/2/3/img2.png]]
![[Base/1/2/3/img3.png]]
```cpp
#include <iostream>
using namespace std;

int main()
{
    int number;

    // Здесь будет твой код

    cin >> number;
    cout << "Привет из школы №" << number << "!";
}
```
![[Base/1/2/3/img4.png]]
```cpp
#include <iostream>
using namespace std;

int main()
{
    int a, b; // Два слагаемых

    // Сначала ввод данных, потом получение ответа

    cin >> a;    
    cin >> b;
    cout << a << " + " << b << " = " << a + b;
}
```
![[Base/1/2/3/img5.png]]
```cpp
#include <iostream>
using namespace std;

int main()
{
    // Твой код должен быть где-то здесь

    float a, b;
    
    cin >> a;
    cin >> b;
    
    cout << "Периметр: " << 2 * (a + b) << endl;
    cout << "Площадь: " << a * b << endl;
}
```
![[Base/1/2/3/img6.png]]
```cpp
#include <iostream>
using namespace std;

int main()
{
    // Хочешь поделить оценку и получить дробное число?
    // Так используй тип данных float!
    
    float a, b, c;
    
    cin >> a;
    cin >> b;
    cin >> c;
    
    cout << "Твоя оценка - " << (a + b + c) / 3 << endl;
}
```