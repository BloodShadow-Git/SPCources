![[Base/1/5/3/img1.png]]
```cpp
#include <iostream>
using namespace std;

int main()
{
    // ↓ Вот твой массив ↓
    float numbers[7] = {1.6, 2.8, 3, -3.141, 451, -0.5, 0.66};

    // Здесь будет твой код . . . 
    for (const auto& item : numbers) {
        cout << item << " ";
    }
}
```
![[Base/1/5/3/img2.png]]
```cpp
#include <iostream>
using namespace std;

int main()
{
    int numbers[24];

    // Здесь будет твой код . . . 

    // Код для вывода массива
    // (НЕ ИЗМЕНЯТЬ!)
    for (int num : numbers)
    {
        cin >> num;
        cout << num << " ";
    }
}
```
![[Base/1/5/3/img3.png]]
```cpp
#include <iostream>
#include <limits.h>
using namespace std;

int main()
{
    int numbers[20];
    int max = INT_MIN;

    for (int& num : numbers)
    {
        cin >> num;
        if (num > max) { max = num; }
    }
    cout << max << endl;
    // Здесь будет твой код . . . 
}
```
![[Base/1/5/3/img4.png]]
```cpp
#include <iostream>
using namespace std;

int main()
{
    int numbers[10];
    int res = 0;
    
    for (int& num : numbers)
    {
        cin >> num;
        if (num % 2 != 0) { res += num; }
    }
    cout << res << endl;
    // Здесь будет твой код . . . 
}
```