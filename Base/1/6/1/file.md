![[Base/1/6/1/img1.png]]
![[Base/1/6/1/img2.png]]
![[Base/1/6/1/img3.png]]
![[Base/1/6/1/img4.png]]
```cpp
#include <iostream>
using namespace std;

int main()
{
    cout << "Двойная кавычка: \"" << endl
         << "Одинарная кавычка: " << '\'' << endl
         << "Перенос строки: \n" << endl
         << "Горизонтальный отступ: ->\t<-" << endl
         << "Обратная косая черта: \\" << endl;
}
```
![[Base/1/6/1/img5.png]]
```cpp
// ↓ Вот твой массив ↓
char hello[] = "Hello world!";

// Только не используй cout!
```
![[Base/1/6/1/img6.png]]
```cpp
#include <iostream>
using namespace std;

int main()
{
    char name[100];
    cin >> name;
    cout << "Привет, " << name << "!";
}
```
![[Base/1/6/1/img7.png]]
```cpp
#include <iostream>
using namespace std;

void reverseArray(char* arr, int n) {
    for (int i = 0; i < n / 2; i++) {
        swap(arr[i], arr[n - i - 1]);
    }
}

int main()
{
    int length;
    cin >> length;

    char word[length + 1];
    cin >> word;
    // Здесь будет твой код . . . 
    reverseArray(word, length);
    cout << word;
}
```
![[Base/1/6/1/img8.png]]
```cpp
#include <iostream>
using namespace std;

int main()
{
    // Поэкспериментируем?
    char strings[][100] = {
        "Пончики - это просто бублики с посыпкой",
        "Клубничный монстр",
        "Тарталетки с брусникой",
        "КРЕВЕТКИ ЗАХВАТЯТ МИР!",
        "Крабонатор"
    };

    // Код для вывода массива
    // НЕ ИЗМЕНЯТЬ!
    for (char (&str)[100] : strings)
    {
        cout << str << endl;
    }
}
```
![[Base/1/6/1/img9.png]]
```cpp
#include <iostream>
using namespace std;

int main()
{
    int length;
    cin >> length;

    char word[length + 1];
    cin >> word;
    
    // Здесь будет твой код . . . 
    bool isPal = true;
    for (int i = 0; i < length / 2; i++) {
        if (word[i] != word[length - i - 1]) {
            isPal = false;
            break;
        }
    }
    cout << (isPal ? "Да" : "Нет");
}
```
