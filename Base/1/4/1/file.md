![[Base/1/4/1/img1.png]]
`0 1 2 3 4`
![[Base/1/4/1/img2.png]]
![[Base/1/4/1/img3.png]]
`5 14 23`
![[Base/1/4/1/img4.png]]
```cpp
#include <iostream>
using namespace std;

int main()
{
    for (int i = 1; i < 34; i++)
    {
        cout << i << endl;
    }
}
```
![[Base/1/4/1/img5.png]]
```cpp
#include <iostream>
using namespace std;

int main()
{
    for (int i = 20; i <= 100; i += 2){
        cout << i << endl;
    }
}
```
![[Base/1/4/1/img6.png]]
```cpp
#include <iostream>
using namespace std;

int main()
{
    float sum = 0; // Сумма всех масс

    for (int i = 0; i < 15; i++)
    {
        float mass;
        cin >> mass;
        sum += mass;
    }
    cout << sum << endl;
}
```
![[Base/1/4/1/img7.png]]
```cpp
#include <iostream>
using namespace std;

int main()
{
    int max = 0;
    
    int current;
    for(int i = 0; i < 16; i++){
        cin >> current;
        if (current > max) { max = current; }
    }
    cout << max << endl;
}
```
![[Base/1/4/1/img8.png]]
```cpp
#include <iostream>
using namespace std;

int main()
{
    for (int i = 1; i < 14; i++)
    {
        cout << i << endl;
        if (i % 5 == 0) { cout << "Бип!!" << endl; }
    }
}
```