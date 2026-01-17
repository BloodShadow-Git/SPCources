![[Base/1/5/2/img1.png]]
```cpp
#include <iostream>
using namespace std;

int main()
{
    // ↓ Вот твой массив ↓
    int numbers[10] = {1, 2, 3, -3, -2, -1, 0, 4, 5, 6};

    // Выведи элементы этого массива . . . 
    for (int i = 0; i < 10; i++) {
        cout << numbers[i] << " ";
    }
}
```
![[Base/1/5/2/img2.png]]
```cpp
#include <iostream>
using namespace std;

int main()
{
    int numbers[16];

    // Здесь будет твой код . . . 

    // Код для вывода массива
    // (НЕ ИЗМЕНЯТЬ!)
    for (int i = 0; i < 16; ++i)
    {
        cin >> numbers[i];
        cout << numbers[i] << " ";
    }
}
```
![[Base/1/5/2/img3.png]]
```cpp
#include <iostream>
#include <cmath>
using namespace std;

int main()
{
    int squares[30];

    // Здесь будет твой код . . . 

    // Код для вывода массива
    // (НЕ ИЗМЕНЯТЬ!)
    for (int i = 0; i < 30; ++i)
    {
        squares[i] = pow(i, 2);
        cout << squares[i] << " ";
    }
}
```
![[Base/1/5/2/img4.png]]
```cpp
#include <iostream>
using namespace std;

int main()
{
    // Здесь будет твой код . . . 
    const int ARRAY_SIZE = 7;    
    int array[ARRAY_SIZE];
    
    for (int i = 0; i < ARRAY_SIZE; i++) {
        cin >> array[i];
    }
    for (int i = ARRAY_SIZE - 1; i >= 0; i--) {
        cout << array[i] << " ";
    }
}
```
![[Base/1/5/2/img5.png]]
```cpp
#include <iostream>
#include <vector>
#include <unordered_map>

using namespace std;

int main() {
    unordered_map<int, int> countMap;
    
    for (int i = 0; i < 13; ++i) {
        int num;
        cin >> num;
        countMap[num]++;
    }
    
    int uniqueCount = 0;
    for (const auto& pair : countMap) {
        if (pair.second == 1) {
            uniqueCount++;
        }
    }
    
    cout << "Уникальных чисел найдено " << uniqueCount << endl;
    
    return 0;
}
```
![[Base/1/5/2/img6.png]]
```cpp
#include <iostream>
#include <vector>
#include <unordered_map>

using namespace std;

int main() {
    unordered_map<int, int> countMap;
    
    for (int i = 0; i < 13; ++i) {
        int num;
        cin >> num;
        countMap[num]++;
    }
    
    int uniqueCount = 0;
    for (const auto& pair : countMap) {
        if (pair.second > 1) {
            uniqueCount += pair.second - 1;
        }
    }
    
    cout << "Дубликатов найдено " << uniqueCount << endl;
    
    return 0;
}
```