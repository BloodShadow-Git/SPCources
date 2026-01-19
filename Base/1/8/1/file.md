![[Base/1/8/1/img1.png]]
![[Base/1/8/1/img2.png]]
![[Base/1/8/1/img3.png]]
```cpp
#include <iostream>
#include <string>
#include <fstream>
//        ↑↑↑
// Не забудь про это

using namespace std;

int main()
{
    ifstream myfile("hello-world.txt");
    string txt;
    getline(myfile, txt);
    cout << txt;
    // Покажи, на что способен!
}
```
![[Base/1/8/1/img4.png]]
```cpp
#include <iostream>
#include <string>
#include <fstream>
using namespace std;

int main()
{
    string txt;
    cin >> txt;
    ifstream file(txt);

    // Ну что? Вернёмся к допотопным циклам?
    for (int i = 0; i < 3; i++) {
        file >> txt;
        cout << txt << " ";
    }
}
```
![[Base/1/8/1/img5.png]]
```cpp
#include <iostream>
#include <fstream>
#include <string>
using namespace std;

int main()
{    
    string buf;
    cin >> buf;
    ifstream r(buf);
    
    for (int i = 0; i < 3; i++) {
        getline(r, buf);
        cout << buf << endl;
    }
}
```
![[Base/1/8/1/img6.png]]
```cpp
#include <iostream>
#include <fstream>
#include <string>
#include <algorithm>
using namespace std;

int main()
{
    string filename;
    cin >> filename;

    ifstream file(filename);

    // Здесь будет твой код . . . 
    int a;
    int b;
    file >> a;
    file >> b;
    cout << max(a, b) << endl;
}
```
![[Base/1/8/1/img7.png]]
![[Base/1/8/1/img8.png]]
```cpp
#include <iostream>
#include <fstream>
#include <string>
using namespace std;

int main()
{
    // Здесь будет твой код . . . 
    string buf;
    cin >> buf;
    ifstream r(buf);
    if (r.is_open()) { cout << "Файл существует" << endl; }
    else { cout << "Файл не найден" << endl; }
}
```