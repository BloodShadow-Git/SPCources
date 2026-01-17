![[Base/1/4/2/img1.png]]
![[Base/1/4/2/img2.png]]
![[Base/1/4/2/img3.png]]
```cpp
#include <iostream>
using namespace std;

int main()
{
    float sum = 0;
    float mass;
    do{
    cin >> mass;
        if(mass > 0){sum+=mass;}
    }    
    while (mass != 0);
    
    cout << sum << endl;
}
```
![[Base/1/4/2/img4.png]]
```cpp
#include <iostream>
using namespace std;

int main()
{
    int a;
    int sum = 0;
    cin >> a;
    
    while(a>10){
            sum += a % 10;
        a = a / 10;
    }
    sum += a;
    
    cout << sum << endl;
}
```
![[Base/1/4/2/img5.png]]
```cpp
#include <iostream>
using namespace std;

int main()
{
    int a;
    
    cin >> a;
    
    while(a > 9){
        cout << a % 10;
        a /= 10;
    }
    cout << a;
    
    cout << endl;
}
```