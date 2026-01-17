![[Base/1/4/4/img1.png]]
```cpp
#include <iostream>
using namespace std;

int main()
{
    int num; // Исходное число
    int fac = 1; // Факториал числа (ответ)

    // Здесь будет твой код . . . 
    cin >> num;
    
    for (; num > 1; num--) {
        fac *= num;
    }
    cout << fac << endl;
}
```
![[Base/1/4/4/img2.png]]
```cpp
#include <iostream>
using namespace std;

int main()
{
    // Здесь будет твой код . . . 
    int iterCount = 1;
    cin >> iterCount;
    int res = 0;
    
    int buffer;
    for (;iterCount > 0; iterCount--) {
        cin >> buffer;
        if (buffer > 0) { res++; }
    }
    cout << res << endl;
}
```
![[Base/1/4/4/img3.png]]
```cpp
#include <iostream>
using namespace std;

int main()
{
    // Первые 2 числа a и b
    int prev = 0;
    int cur = 1;

    cout << prev << " " << cur;
    
    // Не забудь вывести первые 2 числа

    // Здесь будет твой код . . . 
    int buffer;
    for (int i = 0; i < 30; i++) {
        buffer = prev + cur;
        cout << " " << buffer;
        prev = cur;
        cur = buffer;
    }
}
```
![[Base/1/4/4/img4.png]]
```cpp
#include <iostream>
using namespace std;

int main()
{
    // Не забудь инициализировать переменную с суммой
    int start = 0;
    int end = 1;
    int res = 1;

    cin >> start >> end;
    res = start;
    // Здесь будет твой код . . .
    for (int i = start + 1; i < end + 1; i++) {
        res += i;
    }
    cout << res << endl;
}
```
![[Base/1/4/4/img5.png]]
```cpp
#include <iostream>
#include <cmath>
using namespace std;

int main()
{
    // Здесь будет твой код . . . 
    int number = 1;
    int step = 1;
    
    cin >> number >> step;
    
    for (int i = 1; i < step + 1; i++) {
        cout << number << " в " << i << "-й степени равно " << pow(number, i) << endl;
    }
}
```