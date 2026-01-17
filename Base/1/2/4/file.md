![[Base/1/2/4/img1.png]]
```cpp
#include <cmath>
```
![[Base/1/2/4/img2.png]]
![[Base/1/2/4/img3.png]]
```cpp
#include <iostream>
using namespace std;

int main()
{
    // Здесь будет твой код . . . 
    
    float a, b;
    
    cin >> a >> b;
    cout << "Сумма чисел: " << a + b << endl << "Разность чисел: " << a - b << endl << "Произведение чисел: " << a * b << endl << "Частное от деления чисел: " << a / b << endl;
}
```
![[Base/1/2/4/img4.png]]
```cpp
#include <iostream>
//        ↓↓↓
#include <cmath>
using namespace std;

int main()
{
    int a, b;
    
    cin >> a >> b;
    cout << "Расстояние равно " << max(a, b) - min(a, b) << endl;
}
```
![[Base/1/2/4/img5.png]]
```cpp
#include <iostream>
#include <cmath>
using namespace std;

int main()
{
    // Здесь будет твой код . . .
    int a;
    cin >> a;
    cout << "У этого монитора сторона " << sqrt(a) << " пикселей" << endl;
}
```
![[Base/1/2/4/img6.png]]
```cpp
#include <iostream>
#include <cmath>
using namespace std;

int main()
{
    // Здесь будет твой код . . . 

    // Скопируй текст, который нужно вывести
    // Лучше не печатай его вручную!
    int a;
    cin >> a;
    cout << "Вторая степень: " << pow(a, 2) << "\nТретья степень: " << pow(a, 3) << "\nЧетвертая степень: " << pow(a, 4) << "\nПятая степень: " << pow(a, 5) << endl;
}
```