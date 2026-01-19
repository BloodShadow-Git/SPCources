![[Base/1/8/3/img1.png]]
![[Base/1/8/3/img2.png]]
![[Base/1/8/3/img3.png]]
```cpp
#include <iostream>
#include <string>
#include <fstream>
using namespace std;

// Функция для печати файла
// НЕ ИЗМЕНЯТЬ!
void print_file()
{
    ifstream myfile("одуванчики.txt", ios::ate);

    int size = myfile.tellg();
    myfile.seekg(0);

    char content[size];
    myfile.read(content, size);

    // Невероятно, но так тоже можно
    cout.write(content, size);
}

int main()
{
    ofstream myfile("одуванчики.txt");

    // Здесь будет твой код . . . 
    myfile << "С новым 1928 годом!" << endl;
    myfile.flush();
    myfile.close();
    // Не забудь сбросить данные на диск
    // Перед вызовом функции print_file

    print_file();
}
```
![[Base/1/8/3/img4.png]]
```cpp
#include <iostream>
#include <string>
#include <fstream>
using namespace std;

// Функция для печати файла
// НЕ ИЗМЕНЯТЬ!
void print_file()
{
    ifstream myfile("hello-world.txt", ios::ate);

    int size = myfile.tellg();
    myfile.seekg(0);

    char content[size];
    myfile.read(content, size);

    cout.write(content, size);
}

int main()
{
    ofstream myfile("hello-world.txt");
    char hello_text[39] = "Привет тебе из файла!";

    // Здесь будет твой код . . . 
    myfile << hello_text;
    myfile.flush();
    myfile.close();
    // Не забудь сбросить данные на диск
    // Перед вызовом функции print_file

    print_file();
}
```
![[Base/1/8/3/img5.png]]
```cpp
#include <iostream>
#include <string>
#include <fstream>
using namespace std;

int main()
{
    // Здесь будет твой код . . . 

    // Просто скопируй свой код из задания урока 3.2
    // А затем замени cout на переменную с файлом
    int a;
    cin >> a;
    
    ofstream w("output.txt");
    if (a >= 100 && a <= 999) { w << "Yes" << endl; }
    else { w << "No" << endl; }
}
```
![[Base/1/8/3/img6.png]]
```cpp
#include <iostream>
#include <string>
#include <fstream>
using namespace std;

int main()
{
    // Здесь будет твой код . . . 

    // Просто скопируй свой код из задания урока 4.4
    // А затем замени cout на переменную с файлом
    int prev = 0;
    int cur = 1;
    
    ofstream w("Fibonacci.txt");
    w << prev << " " << cur;
    
    int buffer;
    for (int i = 0; i < 28; i++){
        buffer = prev + cur;
        w << " " << buffer;
        prev = cur;
        cur = buffer;
    }
}
```