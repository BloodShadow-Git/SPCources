# 1
![[Tasks/1/img1.png]]
```cpp
#include <iostream>
using namespace std;
int main(){
  int a, b;
  cin >> a >> b;
  cout << b << " " << a << endl;
  return 0;  
 }
```
# 2
![[Tasks/1/img2.png]]
```cpp
#include <iostream>
using namespace std;
int main(){
  int a, b, c;
  cin >> a >> b >> c;
  cout << a + b + c << endl;
  cout << a * b * c << endl;
  return 0;  
 }
```
# 3
![[Tasks/1/img3.png]]
```cpp
#include <iostream>
#include <cmath>
using namespace std;
int main(){
  int a, b;
  cin >> a >> b;  
  cout << 4 * pow(a*a - 5*b, 2) << endl;
  return 0;  
 }
```
# 4
![[Tasks/1/img4.png]]
```cpp
#include <iostream>
using namespace std;
int main(){
  int x, a, b, c;  
  cin >> x;
  a = x / 100;
  b = (x % 100) / 10;
  c = x % 10;
  cout << a + b + c << endl;
  return 0;   
 }
```
# 5
![[Tasks/1/img5.png]]
```cpp
#include <iostream>
using namespace std;
int main(){
  int a, b, c;
  cin >> a >> b >> c; 
  cout << a*a + b*b + c*c << endl;
  return 0;
 }
```
# 6
![[Tasks/1/img6.png]]
```cpp
#include <iostream>
using namespace std;
int main(){
  int x, a, b, c, d;
  cin >> x;
  a = x / 1000;
  b = x / 100 % 10;
  c = x / 10 % 10;
  d = x % 10;
  if (d != 0) { cout << d; }
  if (c != 0 || d != 0) { cout << c; }
  if (b != 0 || c != 0 || d != 0) { cout << b; }
  if (a != 0 || b != 0 || c != 0 || d != 0) { cout << a; }
  cout << endl;
  return 0;
 }
```
# 7
![[Tasks/1/img7.png]]
```cpp
#include <iostream>
using namespace std;
int main(){
  int x, a, b, c, d, e;
  cin >> x;
  a = x / 10000;
  b = x / 1000 % 10;
  c = x / 100 % 10;
  d = x / 10 % 10;
  e = x % 10;  
  cout << a << " " << b << " " << c << " " << d << " " << e << endl;
  return 0;
 }
```
# 8
![[Tasks/1/img8.png]]
```cpp
#include <iostream>
using namespace std;
int main(){
  int x, a, b, c, d, p, r;
  cin >> x;
  a = x / 1000;
  b = x / 100 % 10;
  c = x / 10 % 10;
  d = x % 10;
  p = b * 10 + a;
  r = d * 10 + c;
  cout << p << " + " << r << " = " << p + r << endl; 
  return 0;  
 }
```
# 9
![[Tasks/1/img9.png]]
```cpp
#include <iostream>

using namespace std;

int main() {
    int x, a, b, c, d, e;
    cin >> x;
    a = x / 10000;
    b = x / 1000 % 10;
    c = x / 100 % 10;
    d = x / 10 % 10;
    e = x % 10;
    cout << 16*a + 8*b + 4*c + 2*d + e << endl;
    
    return 0;
}
```