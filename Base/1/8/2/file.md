![[Base/1/8/2/img1.png]]
![[Base/1/8/2/img2.png]]
```cpp
#include <iostream>
#include <fstream>
using namespace std;

int main()
{
    string buf;
    cin >> buf;
    ifstream r(buf, ios::ate);
    cout << r.tellg();
    // Здесь будет твой код . . . 
}
```
![[Base/1/8/2/img3.png]]
```cpp
#include <iostream>
#include <string>
#include <fstream>
#include <vector>
using namespace std;

int main()
{
    ifstream r("Задание 6-2-4.txt");

    int pos;
    int count;
    cin >> pos >> count;
    char buf[count+1] = {0};
    r.seekg(pos);
    r.read(buf, count);
    cout << buf << endl;
    // Здесь будет твой код . . . 
}
```
![[Base/1/8/2/img4.png]]
```cpp
#include <iostream>
#include <string>
#include <fstream>
using namespace std;

int main()
{
    string buf;
    cin >> buf;

    ifstream r(buf, ios::ate);

    // Здесь будет твой код . . .
    int size = r.tellg();
    r.seekg(0);
    char c[size + 1] = {0};
    r.read(c, size);
    cout << c << endl;
}
```
![[Base/1/8/2/img5.png]]
```cpp
#include <iostream>
#include <string>
#include <fstream>
using namespace std;

int main()
{
    string buf;
    cin >> buf;

    ifstream r(buf);

    // Здесь будет твой код . . .
    if (r.is_open()) {
        r.close();
        r.open(buf, ios::ate);
        int size = r.tellg();
        r.seekg(0);
        char c[size + 1] = {0};
        r.read(c, size);
        cout << c << endl;
    }
    else { cout << "Файл не существует" << endl; }
}
```