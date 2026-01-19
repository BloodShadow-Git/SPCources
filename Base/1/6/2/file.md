![[Base/1/6/2/img1.png]]
![[Base/1/6/2/img2.png]]
```cpp
#include <iostream>
//        ↓↓↓
#include <string>
using namespace std;

int main()
{
    char name[100];
    cin >> name;
    cout << "Привет, " << name << "!";
}
```
![[Base/1/6/2/img3.png]]
```cpp
#include <iostream>
#include <string>
using namespace std;

int main()
{
    // Здесь будет твой код . . . 
    string txt;
    getline(cin, txt);
    cout << "Здравствуйте, " << txt << "!";
}
```
![[Base/1/6/2/img4.png]]
```cpp
#include <iostream>
#include <string>
using namespace std;

int main()
{
    string txt;
    getline(cin, txt);
    
    for (int i = 0; i < txt.length() / 2; i++) {
        swap(txt[i], txt[txt.length() - i - 1]);
    }
    cout << txt;
}
```
![[Base/1/6/2/img5.png]]
![[Base/1/6/2/img6.png]]
```cpp
// ↓ Вот твоя строка ↓
string love;
cin >> love;

// Измени её
// НЕ создавай новую строку!
// НЕ используй cout!
love.insert(0, "I love you, ");
love.append("!");
// В этом заданиие не требуется функция main
```
![[Base/1/6/2/img7.png]]
```cpp
#include <iostream>
#include <string>
using namespace std;

int main()
{
    // Здесь будет твой код . . . 
    string txt;
    getline(cin, txt);
    string bal;
    getline(cin, bal);
    
    size_t pos = 0;
    const string marker = "<-here->";
    
    while ((pos = txt.find(marker, pos)) != string::npos) {
        txt.replace(pos, marker.length(), bal);
        pos += bal.length();
    }
    
    // Выводим результат
    cout << txt << endl;
}
```