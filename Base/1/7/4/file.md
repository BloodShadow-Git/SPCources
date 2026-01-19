![[Base/1/7/4/img1.png]]
```cpp
#include <iostream>
using namespace std;

// ↓ Создай здесь функцию fac ↓

int fac(int n) {
    int res = 1;
    for (int i = 1; i <= n; i++) {
        res *= i;
    }
    return res;
}

int main()
{
    int num;
    cin >> num;

    // Вызов функции (не трогай это)
    cout << fac(num);
}
```
![[Base/1/7/4/img2.png]]
```cpp
#include <iostream>
using namespace std;

// ↓ Создай здесь функцию fib ↓

int fib(int e) {
    if (e == 1) { return 0; }
    if (e == 2) { return 1; }
    
    int prev = 0;
    int cur = 1;
    
    int buffer;
    for (int i = 3; i <= e; i++) {
        buffer = prev + cur;
        prev = cur;
        cur = buffer;
    }
    return buffer;
}

int main()
{
    int num;
    cin >> num;

    // Вызов функции (не трогой это!)
    cout << fib(num);
}
```
![[Base/1/7/4/img3.png]]
```cpp
#include <iostream>
using namespace std;

// ↓ Напиши здесь функцию sum_digits ↓

int sum_digits(int i) {
    int sum = 0;
    
    while (i > 0) {
        sum += i % 10;
        i /= 10;
    }
    
    return sum;
}

int main()
{
    int number;
    cin >> number;

    // Вызов функции (не изменять)
    cout << sum_digits(number);
}
```