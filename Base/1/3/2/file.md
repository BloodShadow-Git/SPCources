![[Base/1/3/2/img1.png]]
![[Base/1/3/2/img2.png]]
![[Base/1/3/2/img3.png]]
```cs
// C#

int x = 4;
int y = 10;
int z = -3;

Console.WriteLine(!(x == 4 && y == 10));
Console.WriteLine(!(x != 4));
Console.WriteLine(x > 0 && x < 10);
Console.WriteLine(x == y - 10 || -z != 3);
Console.WriteLine(y % 2 == 0 && x % 2 != 0);
Console.WriteLine(x < 0 || z < 0);
```
![[Base/1/3/2/img4.png]]
```cpp
#include <iostream>
using namespace std;

int main()
{
    // Здесь будет твой код . . . 
    int a, b;
    cin >> a >> b;
    
    if (a > 6) {
        if (b < 300) { cout << "No" << endl; return 0; }
    }
    cout << "Yes" << endl;
    return 0;
}
```
![[Base/1/3/2/img5.png]]
```cpp
#include <iostream>
using namespace std;

int main()
{
    // Здесь будет твой код . . . 
    int a;
    cin >> a;
    
    if (a >= 100 && a <= 999) { cout << "Yes" << endl; }
    else { cout << "No" << endl; }
}
```