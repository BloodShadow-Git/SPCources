![[Base/1/7/3/img1.png]]
```cpp
#include <iostream>
using namespace std;

// Скопируй код функций из прошлых заданий (ctrl+c ctrl+v)

bool is_leap_year(int a)
{
    return a % 4 == 0 && a % 100 != 0 || a % 400 == 0;
}

int get_days(int m, int a) {
    int days[12] = { 31, 28, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31 };
    if(is_leap_year(a)&&m==2){return days[m - 1]+1;}
    else{return days[m - 1];}
}

// Затем чуть-чуть измени код функции get_days

int main()
{
    int month, year;

    cin >> month;
    cin >> year;

    // Вызов функции (не изменять)
    cout << get_days(month, year);
}
```
![[Base/1/7/3/img2.png]]
```cpp
#include <iostream>
using namespace std;

// Скопируй функции из прошлого задания (ctrl+c ctrl+v)

bool is_leap_year(int a)
{
    return a % 4 == 0 && a % 100 != 0 || a % 400 == 0;
}

int get_days(int m, int a) {
    int days[12] = { 31, 28, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31 };
    if(is_leap_year(a)&&m==2){return days[m - 1]+1;}
    else{return days[m - 1];}
}

// ↓ Напиши здесь свою функцию ↓
bool is_valid_date(int day, int month, int year)
{
    if(day<=0||month>12){return false;}
    return day <= get_days(month, year);
}

int main()
{
    int day, month, year;

    cin >> day;
    cin >> month;
    cin >> year;

    // Вызов функции (не изменять)
    if (is_valid_date(day, month, year)) {
        cout << "Yes";
    }
    else {
        cout << "No";
    }
}
```
![[Base/1/7/3/img3.png]]
```cpp
#include <iostream>
using namespace std;

void print_side(int width) // Рисует одну строчку горизонтальной части
{ cout << string(width, '#') << endl; }
void print_body(int width) // Рисует одну строчку вертикальной части
{ cout << '#' << string(width - 2, ' ')<< '#' << endl; }
    
void print(int width, int height) // Рисует всю рамку в целом через цикл
{
    if(height==0){return;}
    if(height-1>0){print_side(width);}
    for(int i = 0; i < height - 2; i++){
        print_body(width);
    }
    print_side(width);
}
    
// Прочитай повнимательнее блок Выходные данные

int main()
{
    int width, height;
    cin >> width;
    cin >> height;

    // Вызов функции (не трогать)
    print(width, height);
}
```
![[Base/1/7/3/img4.png]]
```cpp
#include <iostream>
#include <cmath>
using namespace std;

// ↓ Здесь будет твоя функция ↓
bool is_prime(int n) {
    // Обрабатываем отрицательные числа и 0, 1 — они не простые
    if (n <= 1) {
        return false;
    }
    
    // Проверяем делители от 2 до sqrt(n)
    for (int i = 2; i <= sqrt(n); ++i) {
        if (n % i == 0) {
            return false;
        }
    }
    
    return true;
}

int main()
{
    int num;
    cin >> num;

    // Вызов функции (не трогать)
    if (is_prime(num)) {
        cout << "ДА";
    }
    else {
        cout << "НЕТ";
    }
}
```