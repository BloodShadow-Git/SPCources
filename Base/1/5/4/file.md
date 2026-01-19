![[Base/1/5/4/img1.png]]
![[Base/1/5/4/img2.png]]
![[Base/1/5/4/img3.png]]
```cpp
// ↓ Вот твой массив ↓
float space[3][2][4];
```
![[Base/1/5/4/img4.png]]
```cpp
// Сейчас это пустая матрица
int matrix[3][5] = {
    { -45, -46, 39, 40, 48 },
    { -43, -34, 48, -46, 40 },
    { 33, -39, -46, -45, 30 }
};
// Задай ей размеры и заполни значениями
```
![[Base/1/5/4/img5.png]]
```cpp
#include <iostream>
using namespace std;

int main()
{
    // Вот твоя матрица
    // (НЕ ИЗМЕНЯТЬ!)
    int matrix[3][3] = {
        {3, 5, 8},
        {53, 46, 81},
        {-435, -235, -285}
    };

    // Здесь будет твой код . . . 
    for (auto& x : matrix) {
        for (auto& y : x) {
            cout << y << " ";
        }
        cout << endl;
    }
}
```