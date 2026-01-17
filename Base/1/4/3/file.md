![[Base/1/4/3/img1.png]]
```cpp
for (int i = 1; i <= 3; ++i)
{
    for (int j = -1; j >= -3; --j)
    {
        cout << i << " " << j << endl;
    }
}
```
![[Base/1/4/3/img2.png]]
![[Base/1/4/3/img3.png]]
```cpp
#include <iostream>
using namespace std;

int main()
{  
    int a;
    cin >> a;
    for (int i = 1; i <= a; i++)
    {
        cout << "Неделя №" << i << endl;

        for (int j = 1; j < 8; j++)
        {
            cout << "День №" << j << endl; 
        }
    }
}
```
![[Base/1/4/3/img4.png]]
```cpp
#include <iostream>
using namespace std;

int main()
{
    int a, b;
    cin >> a >> b;
    
    for(int i = 0; i < b; i++){
        for(int j = 0; j < a; j++){
            cout << '*';
        }
        cout << endl;
    }
}
```
![[Base/1/4/3/img5.png]]
```cpp
#include <iostream>
using namespace std;

int main()
{
    int a;
    cin >> a;
    
    for(int i = 0; i < a; i++){
        cout << string(a - i, '*') << endl;
    }
}
```
![[Base/1/4/3/img6.png]]
```cpp
#include <iostream>
using namespace std;

int main()
{
    int a;
    cin >> a;
    a /= 2;
    
    // Расширение вверх
    for (int i = 1; i <= a + 1; i++) {
        for (int j = 0; j < i; j++) {
            cout << "*";
        }
        cout << endl;
    }
    
    // Сужение вниз  
    for (int i = a; i >= 1; i--) {
        for (int j = 0; j < i; j++) {
            cout << "*";
        }
        cout << endl;
    }
}
```